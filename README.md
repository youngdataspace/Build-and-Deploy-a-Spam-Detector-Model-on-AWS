# Artificial Neural Network (ANN) Classifier + Deployment on AWS Cloud Servers
In this post, we will build a spam message classifier and deploy it. First, we will train and evaluate an Artificial Neural Network (ANN) model locally. Once we are satisfied with our model, we will deploy it on AWS using SageMaker. 

This repository contains all the codes necessary to replicate the contents in <a href = "https://medium.com/@y.s.yoon/artificial-neural-network-ann-classifier-deployment-on-aws-cloud-servers-405254909161">this blog post</a>. If you have any comments or suggestions, email me at y.s.yoon@berkeley.edu.

# Part 1 - Build a spam classifier locally (spam_classifier.ipynb)

## Virtual Environment
Once we build a deep learning model using TensorFlow, we will deploy it on AWS using SageMaker. However, the version of SageMaker's TensorFlow is 1.15.5 at the time of this writing. This means that we have to use Python 3.7. For those of you who have Python 3.8 like me, it is important that we train the model using Python 3.7 on a virtual environment.

1. Type the following in Anaconda Prompt</br>
"conda create -n python37 python=3.7"


2. Activate the python37 virtual environment</br>
"conda activate python37"</br>
By the way, we can deactivate the virtual environment by typing "conda deactivate" but lets leave it as active for now.</br>


3. Install necessary packages in the environment. For TensorFlow, let's match the version with the SageMaker's version.
pip install tensorflow==1.15.5
pip install pandas
pip install matplotlib


4. Make the environment available in Jupyter Notebook</br>
"pip install ipykernel"</br>
"ipython kernel install --user --name=python37"</br>

These will allow us to use the python37 kernel in Jupyter Notebook as shown below.

<img src ="https://github.com/youngdataspace/Build-and-Deploy-a-Spam-Detector-Model-on-AWS/blob/main/image_python37_kernel.JPG?raw=true">

## Build a classifier using Jupyter Notebook
From the above image, click "python37" and create a new notebook using the virtual environment we just created.

Now we are ready to start working with data. Let's dive in.
