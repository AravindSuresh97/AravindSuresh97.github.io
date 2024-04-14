# The difference between a normal computer program (pre-deep learning) and a machine learning model

In the landscape of computational problem-solving, the advent of machine learning represents a paradigm shift from traditional programming approaches. In this short overview, inspired by insights from Jeremy Howard's Fast Ai course, we'll explore the fundamental differences between conventional computer programs and machine learning models.
![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/82ddfd47-3c17-4c3d-943e-e2ecea3d9aec)

**Why are able to create a bird recognition within few minutes?And why not before?**<br>
In the 2012 deep learning systems for analyzing the breast cancer chances in patients, a team of mathematicians, pathologists, and computer scientists got together and developed a ideas for feature list. This list had thousands of relationship features and each one required careful assessment and expertise from different disciplines. They then fed these features into a machine-learning model.
- Even if the system is effective it is very time-consuming and cannot be built easily. 
- The difference with neural networks is that, neural networks do not require us to build these features, they do it for us – we don’t give it features, we ask it to learn features. With neural networks we don’t have to hand code any of these. We start with a random neural network and we feed it example, and have it learn from it.

In former computer programs which were developed before the deep learning era, the program is usually a bunch of conditionals, loops, and setting variables.<br>

<img width="488" alt="image" src="https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/42e90a48-7c20-47ab-b0b3-0405bd2761ab">


In former computer programs which were developed before the deep learning era, the program is usually a bunch of conditionals, loops, and setting variables.<br>

However, the deep-learning model is a bit different. We have both inputs and weights (also called parameters). <br>

<img width="488" alt="image" src="https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/56ed37e8-0315-4a8b-91b9-4b52873f15e2">

The model is not anymore a bunch of loops and conditionals; it’s a mathematical function. In the case of neural networks, it is a mathematical function that takes the input, multiplies it with the weights and adds them up, replaces negatives with zeroes, and does that again for a second set of weights and so forth. 

{% include alert.html text="Therefore the model does not do anything useful until the weights are chosen carefully. " %}

We start off by choosing the weights to be random. Therefore, initially, the model does not do anything useful at all.

Therfore, how can we resolve this. How about updating the weights based on the results?
![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/a9412e27-9e47-4293-8c78-94d11d860051)

- We choose random weights and pass it and the inputs to the model and get the results. Then we decide how good they are. The loss is a number that says how good were the results. <br>
- So using this, we update the weights for the new set which are better than the previous set of weights.<br>
- Therefore, in the new set, even the loss should be a bit better. Iterating this multiple times would make it good.

{% include info.html text="In theory, we can solve anything given enough time and enough data." %}

Once we finish that training procedure, we don’t need that loss anymore, and we can integrate the weights into the model as we are finished changing them.

![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/a99c0ff1-395c-4d01-9664-aed4133ce8c0)

And this looks exactly like our original idea of program.

Happy Deep Learning 🙇‍♂️
