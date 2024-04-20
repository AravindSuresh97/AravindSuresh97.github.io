#  Building and Deploying Deep Learning Models with Hugging Face

## Introduction
Welcome back to the second part of our guide on building and deploying applications with Hugging Face! <br>
In this installment, we'll delve into the process of incorporating a deep learning model into your application and deploying it using Hugging Face's platform.


- To begin, we need a trained deep learning model.
- In our deep learning notebook, we can add code to export our trained Learner.
  ```python
  learn.export('model.pkl')
  ```

- This file will contain all the necessary information to run the model.
  {% include info.html text="This will be saved as a .pkl file, a Python frozen object." %}
  
- After downloading the file to our local machine, we paste it into the directory where our Hugging Face files are stored.

## Loading the Model

In another notebook, instead of training the learner, we use ```load_learner()``` to load the exported model. <br>
We pass in the file name we saved, which returns the learner, containing our unpacked model.

```python
learn = load_learner('model.pkl')
```

{% include info.html text="This contains our un’pkl’ed learner." %}
<br>

## Creating the Gradio Interface:

- Gradio requires a callable function to generate predictions. 
- We define a function that returns a dictionary of categories and their probabilities.
{% include alert.html text="Gradio doesn’t handle Pytorch tensors." %}
  Threfore we have to ensure that all values are converted to normal floats.
  
![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/0171d95d-08c9-4d20-a67f-d12e45d63ef6)


## Building the Interface:
```python
#|export
image = gr.input.Imae(shape=(192,192))
label = gr.outputs.label()
examples = ['dog.jpg', 'cat.jpg', 'dunno.jpg']

intf = gr.Interface(fn=classify_image, inputs=image, outputs=label, examples=examples)
intf.launch(inine=False)
```

- What function do we call to get the output: ```fn=classify_image``` <br>
- What is the input: ```inputs=image``` <br>
- What is the output: ```outputs=label``` <br>

Running the interface provides a URL where our application is hosted, allowing us to test it out.
![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/7df3c125-b36b-4ba6-a763-d4dba46287fc)

On that URL, our application will have been hosted.
![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/bf226131-d443-4c16-8547-3fbe17f9a8c5)

And we can test out the system there:
![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/e1a01625-0f5c-44f5-b84a-67d42388c12d)

Great!! We have it working! <br>


## Converting to a Python Script:
Now to convert that into a Python script, ether we can copy and paste all the parts we need.
What Jeremy has done here is mentioning a label ```#|export``` on top of each cealls that are required for the final Python script.
 ```python
 #|export
```
By marking the necessary cells with ```#|export``` at the top, convert the interface into a Python script by running the ```nbdev.export``` command.

```python
from nbdev.export import notebook2script
notebook2script('app.ipynb')
```
This generates a file with the required scripts, eliminating the need for manual copying and pasting.


## Deploying the Model:

Once we have the app.py file with the required code, we push it to Git and upload it to Hugging Face. <br>
Reloading the Hugging Face space reveals our model running on the provided link. <br>
If set to public, anyone can access and interact with our deployed model.

![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/433f2dd6-10d3-4308-90f7-1b209cd1ea13)



In conclusion, we've demonstrated a simple yet powerful example of getting a deep learning model into production using Hugging Face. <br>
By following these steps, you can deploy your own models and share them with the world.


Happy Hug-Facing 🤟 !
