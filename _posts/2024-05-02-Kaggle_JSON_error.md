# Troubleshooting Kaggle.json Error in Course 22 Repository: A Step-by-Step Guide

Have you ever encountered the perplexing Kaggle.json file error while running the ***08-first-steps-road-to-the-top-part-1*** notebook in the Course 22 repository? 

Don't worry; you're not alone. 

Initially, I found myself scratching my head over this issue, but with the invaluable assistance of ***Brian and Yidi***, we managed to crack the code and resolve it seamlessly.

So, let's delve into the intricacies of resolving this pesky error. 

## Step 1
The first step is to ensure you have a Kaggle account. It doesn't matter whether you use your university email or a personal one to sign up.

<img width="649" alt="image" src="https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/3cc6a39f-f260-4735-a421-a09002a553ac">


## Step 2
- Once you're logged in, navigate to your profile and locate the ***Settings*** option.
  
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/b04f70a2-8693-46e4-bee1-adaf735239a4)


- Under the ***API*** section, you'll find the golden ticket: ***Create New Token***
  
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/ebaf1b00-5d35-4fb2-a0c5-0f57cbe9e70d)
  
- Clicking on this will initiate the download of a ***Kaggle.json*** file, which holds the key to our solution.

 <img width="717" alt="image" src="https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/560dcb86-0224-45da-a3e7-14583129baae">



Now, armed with this file, we need to place it in a specific directory. Let's return to our trusty VS Code and open a bash terminal window. 
Here's where the magic happens:

## Step 3 - Navigate to the Home Directory
In the terminal, type the below command
```python
cd ~ 
```
This will take us to the home directory.

## Step 4 - Access the Kaggle Folder
Now, change to the .kaggle directory.
```python
cd .kaggle/
```
## Step 5 - Create a Kaggle.json File
Use the ```vim``` command to create a new file named kaggle.json. Use the commend:
```python
vim kaggle.json
```
Vim is a powerful text editor that's often pre-installed on Unix-based systems like Linux and macOS.

## Step 6 - Insert Data into the File
Once inside the file, press the ```i``` key to enter insert mode. 
Then paste the copied JSON values from the downloaded Kaggle.json file and paste them into the Vim editor.

The ```i``` command stands for "insert," allowing you to add text to the file.

## Step 7 - Save and Exit Vim
After pasting the data, press the ```Esc``` key to exit insert mode. Then, type
```python
:wq
```
 and hit Enter to save and exit Vim.

```:wq``` is a sequence of commands in Vim that means "write" (save changes) and "quit" (exit Vim).
 

By following these steps and understanding the rationale behind each command, you'll be equipped to tackle the Kaggle.json error head-on. 

Happy trouble-shooting 🤟!
