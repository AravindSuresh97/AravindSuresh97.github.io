# Creating an Application on Hugging Face: A Step-by-Step Tutorial 

1. Introduction to Hugging Face:
- Hugging Face provides a free platform for hosting and sharing machine learning models.
- In this tutorial, we'll learn how to create an application using Hugging Face.
  
2. Setting Up Your Space:
- Start by logging into your Hugging Face account and navigating to the dashboard.
- Click on "New" and select "Space".
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/c402b869-2f98-4cc0-9df5-01693691b547)
  
<br>

  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/fdc30a29-86aa-4826-8a86-af18a5c104e9)


- Give your space a name and choose the ```apache2.0``` license - This allows other peoples to use your work easily, but you don’t have to worry too much about patents.
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/afeb024b-3f46-4501-a9a2-812186f77805)
  <br>
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/86753af2-361a-442d-88c2-03d8dac5ac0c)


- Select the desired SDK. I have chosen Gradio here.

  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/5d04c0a7-e6e9-479c-9eea-9712e043f5a4)

- Decide whether to make your space public or private for sharing.

  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/5ce4ea81-81ae-4a55-b784-6d446326005b)

  
{% include info.html text="I am using screenshots from Jeremy’s video as I am getting errored out from creating a space in Hugging Space." %}
![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/aea606de-1f0a-4b1c-b572-43f3c60653e4)

I will look into why this is happening, and let me know if you are also facing the same issue. <br>
Okay, let’s get back into it.

3. Cloning the Repository:
- After creating your space, clone the repository associated with it.
- Copy the provided git clone command and paste it into your terminal.
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/1630de71-b740-4d12-befa-5c153f369afa)
  <br>
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/02efb85b-1013-429a-8d35-48ec3fb164f0)
  
- After running the git command, we will get a new directory which has the name of our space:<br>

 ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/53e6141a-80ad-444d-8c21-42cb0b01343c)

 
4. Creating the Application:
- Once the repository is cloned, navigate to the newly created directory.
- Create a new file within this directory, named ```app.py```.
- Copy the code provided by Hugging Face for the application and paste it into ```app.py```.
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/25390469-a1bf-4ee4-adaa-e3e210fe208f)

- Open Visual Studio Code for the directory.
- Paste the copied code into the app.py file and save it.
  
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/f95f0434-2a5b-4a77-99ba-d59218baff7f)

- Commit the changes to the Hugging Face repository.
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/4600d04b-dfca-4226-bf33-99ace9f676a1)

  
5. Understanding the Code:
```python
import gradio as gr
def greet(name): return f”Hello {name}!”
gr.Interface(fn=greet,inputs=”text”,outputs=”text”).launch()
```
It will have a gradio interface – ```gr.interface```<br>
With a text input  - ```inputs=”text”```<br>
And a text output – ```outputs="text"```<br>
And this is going to run a  function called ‘greet’ on the inputs – ```fn=greet```<br>
And the function greet will return Hello name: ```def greet(name): return f”Hello {name}!”```<br>

6. Testing the Application:
- Return to the Hugging Face website and navigate to your created space.
- Your application should now be available and running within the space.
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/4666d2ac-db0c-44db-8232-54bfea78401f)

- Test the application by providing input and observing the output.
  ![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/e198bade-af34-4d28-aef5-0215c9cec3ff)

Happy Hug-Facing 🤟 !!


