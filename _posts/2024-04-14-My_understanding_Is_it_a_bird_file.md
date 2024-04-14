# A deep dive into Jeremy Howard's "Is it a Bird?" file
I'll be documenting my exploration of the "Is it a bird?" Python workbook from Jeremy Howard's "Practical Deep Learning for Coders" course. This workbook serves as a hands-on introduction to image classification using deep learning techniques.

My plan is to go through the workbook section by section, explaining what I've learned from Jeremy's lesson 1 as I go along.
I'll break down the code step by step and try to make sense of it with Jeremy's teachings. 

Let's get Started !

```python
urls = search_images('bird photos', max_images=1)
urls[0]
```
Here, we are searching for using Duck Duck Go for images of bird photos.
This then provides us with the URL of a bird image we grabbed.

```python
from fastdownload import download_url
dest = 'bird.jpg'
download_url(urls[0], dest, show_progress=False)

from fastai.vision.all import *
im = Image.open(dest)
im.to_thumb(256,256)
```
This notifies and displays the downloaded image. Now we need a system that can recognize things that are bird versus things that are not birds.
Fast download is one of fastai libraries which allows you to fast download URLs. 
im.to_thumb helps you create thumbnails.

```python
download_url(search_images('forest photos', max_images=1)[0], 'forest.jpg', show_progress=False)
Image.open('forest.jpg').to_thumb(256,256)
```
Now we do the same for Forests using the above lines of code.

Its also important to understand that the system works on numbers. Using  [Pixspy](https://pixspy.com/), we can understand how each image is marked as a set of numbers portraying the amounts of red, green and blue colours each pixel contains between the values of 0 to 255. These numbers act as inputs to our program, using which we will try to figure out if this is a bird or not.

```python
searches = 'forest','bird'
path = Path('bird_or_not')
from time import sleep

for o in searches:
    dest = (path/o)
    dest.mkdir(exist_ok=True, parents=True)
    download_images(dest, urls=search_images(f'{o} photo'))
    sleep(10)  # Pause between searches to avoid over-loading server
    download_images(dest, urls=search_images(f'{o} sun photo'))
    sleep(10)
    download_images(dest, urls=search_images(f'{o} shade photo'))
    sleep(10)
    resize_images(path/o, max_size=400, dest=path/o)
```
We actually need a bird, and a non-bird image,for testing this. But we can't actually search for a non-bird image, therefore we choose to search for a Forest image. So it is pictures of forest vs pictures of birds. 

Here we go through each of the values mentioned in the search variable and search for their photos. We download 200 images of each of them. 

We then resize these images to 400 pixels because for computer vision algorithms you don’t need particularly big images and makes it much faster. Because for some big images, opening it itself takes longer time than the neural networks, so resizing them is a good option.

Here the download_images command runs and downloads images in parallel and hence is fairly faster.

Here we are, searching for 'forest photo','forest sun photo', 'forest shade photo', 'bird photo', 'bird sun photo', 'bird shade photo'.


```python
failed = verify_images(get_image_files(path))
failed.map(Path.unlink)
len(failed)
```
When we download images we often get some broken ones. And if we try and model with broken images, the system will not work. <br>
Therefore, we verify the image and unlinks it if it doesn’t work.


```python
dls = DataBlock(
    blocks=(ImageBlock, CategoryBlock), 
    get_items=get_image_files, 
    splitter=RandomSplitter(valid_pct=0.2, seed=42),
    get_y=parent_label,
    item_tfms=[Resize(192, method='squish')]
).dataloaders(path, bs=32)

dls.show_batch(max_n=6)
```
Datablock gives fastai the library all the information it needs to create a computer vision model. Data block is the key thing you should know about if you are going to use different kinds of datasets. It was designed after analysing hundreds of projects and narrowing down the main 5 things that change from project to project. Let's take a look into each parameters mentioned in the Data block.

```python
blocks=(ImageBlock, CategoryBlock),
```
- First thing we say is , what kind of input and output do we have.
We have mentioned that the input is an Image, and the output is a category. <br>
That’s enough for Fastai to know what kind of model to build for you.

```python
get_items=get_image_files, 
```
- get_image_files is a function that returns a list of image files in a path. So everytime it try and find out what to train from, it will use this function.

```python
splitter=RandomSplitter(valid_pct=0.2, seed=42),
```
-	It is critical to set aside some data to test the accuracy of your model and tis is called the validation set. Fast ai won't let you train a model without one. In this case we say randomly set aside, valid_pct=0.2, which is 20% of the data.

```python
get_y=parent_label,
```
-	Next we are telling fastai the correct label of the photo.<br>
  How do we know if it is a bird photo or a forest photo? Using the parent_label. <br>
   The parent_label therefore simply returns the parent folder of a path

```python
item_tfms=[Resize(192, method='squish')]
```
-	Item_tfms are all the bit of code that runs on every item that is every image in this case. So we are asking it to resize each image to 192x192 pixels. <br>
There are two ways to do this, either crop-out or squish it. <br>
We choosing the squish method here.

```python
.dataloaders(path, bs=32)
```
- Data Loaders are the thing pytorch iterates through to grab a bunch of the data at a time. It harnesses the capabilities of the GPU to do this fast.
- The data loader will feed the training algorithm with a bunch of images. We call this bunch as batches or mini batches.

```python
dls.show_batch(max_n=6)
```
-	The show_batch line of code will display a batch of max_n=6, 6 images which it will be using to feed into the model. <br>
show_batch gives you the input image and also its corresponding label. We get this label by calling the parent_label function.

{% include info.html text="Therefore in the end we have an object called dls (data loaders), that contains iterators for pytorch to run through and grab batches of randomly split out training images to train the model with and validation images to test the model with." %}


Check out Tutorial section in the [Fast AI documents](https://docs.fast.ai/) to gain more knowledge into datablocks and different categories.


```python
learn = vision_learner(dls, resnet18, metrics=error_rate)
learn.fine_tune(3)
```
- Run through every photo out of the 400, for the ones that are forest, it's gonna learn more about what a forest looks like, and for the ones that are bird, it is gonna learn more about what a bird looks like. And the total time in the time column, is the time taken to completely do it.
- A ‘learner’ is a critical concept in fast ai, which combines a model, which is the actual neural network we will be training, and the data we used to train it with. Therefore we pass two things here, the data which is dls, and the model. The model is going to be the actual neural network function. Here we are passing resnet18 which is a built-in model of fastai. 
- The reason we can do this so fast is because somebody has already trained this model to recognize 1 million images of over 1000 different types- called the ImageNet dataset. They then made it available o internet for anyone to download. In fastai, these parameters are downloaded for the user when we use one of the models, so that the user is not left with something to start from scratch.
- fine_tune method takes those pre-trained parameters and adjusts them in a controlled way to just teach the model the differences between the dataset it was originally rained for and the current dataset. This is called fine-tuning.
- In the table below, you will see the error rates, and you can see that the error rates keep decreasing, and after a few attempts the error rate is 0 which means it is 100% accurate.
- 
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/8c7527e5-ca37-4214-9a81-0e40ee369ea2)

- So we now have a learner which has a trained model which now has been fine-tuned for the purpose of recognizing bird pictures from forest pictures.
  


```python
is_bird,_,probs = learn.predict(PILImage.create('bird.jpg'))
print(f"This is a: {is_bird}.")
print(f"Probability it's a bird: {probs[0]:.4f}")
```
- Now we pass on the bird image we initially downloaded and check if it is a bird or not; and it shows us the probability of it being a bird.

- The .predict method takes in an image, and this is how you deploy the model. This is going to return whether it is a bird or not as a string and as an integer and also the probability that it is a nonbird or a bird.

**This example shows us how easy it is to run a deep learning system to perform something that was considered impossible some years back and how it takes very less time to do it as well.**  

Happy Coding 🤟 !!!
