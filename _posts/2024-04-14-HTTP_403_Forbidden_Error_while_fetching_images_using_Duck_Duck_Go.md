# Demystifying HTTP 403: Troubleshooting Image Fetching with DuckDuckGo


I've encountered my fair share of HTTP status codes. 
However, few are as perplexing as the infamous 403 error. 

So when I was trying to run the Duck Duck Go search to fetch images of a group of categroies, I got an error: <br>
![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/d6cd8dd4-f913-4a3a-aa03-8ed72b66284d)

**HTTP Error 403: Forbidden** !!!

I initially got this error when I was trying to execute the below lines of code:
```python
categories = ['airplane', 'automobile', 'bird', 'cat', 'deer', 'frog', 'horse', 'ship', 'truck'] 
for category in categories:
    urls = search_images(f'{category} photos', max_images=1)
    dest = f'{category}.jpg'
    download_url(urls[0], dest, show_progress=False)
    sleep(10)  # Pause between searches to avoid over-loading server
    im = Image.open(dest)
    im.to_thumb(256,256)
```

<br>

Not knowing what it was, neither able to find anything useful online which pinpointed a reason,
- I tried restarting the DevContainer
- I tried restarting VS Code
- I tried restarting my laptop

However, none of it made a difference.

In a desperate attempt to troubleshoot, I began removing each category section from the code and performing the search again. To my surprise, the code ran error-free when I removed the category 'dog'.
```python
dest = 'dog.jpg'
urls = search_images('dog photos', max_images=1)
download_url(urls[0], dest, show_progress=False)
```
This discovery baffled me. 
<br>
To test the absurdity further, I attempted to fetch dog images in a separate code cell. And i encountered teh same error

<br>

![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/f497a7a8-5513-48c2-9837-71810b9e5c26)
<br>
However changing the keyword to ```doggy```, executed the code error free: <br>
```python
dest = 'dog.jpg'
urls = search_images('doggy photos', max_images=1)
download_url(urls[0], dest, show_progress=False)
```

![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/686d2f0f-6ac5-4c7c-a3e4-d60ffca6ebee)


Despite my best efforts, the reason behind this peculiar behavior remains elusive. Speculations abound, ranging from a firewall blocking the requests to DuckDuckGo imposing search restrictions. However, what complicates matters further is that I encountered the same issue on both my personal laptop and the university lab computers.

As of now, I haven't been able to pinpoint the exact cause. Perhaps there's a subtle configuration issue, or maybe it's a limitation of DuckDuckGo's search functionality. Whatever the reason, I'm determined to get to the bottom of it.

Rest assured, I'll update this post as soon as I uncover more information. 
<br>Until then, the mystery of the HTTP 403 error persists, leaving me scratching my head in search of answers.

Happy Debugging 🤟 !!!
