# Artificial Neural Network (ANN) Classifier + Deployment on AWS Cloud Servers
In this post, we will build a spam message classifier and deploy it. First, we will train and evaluate an Artificial Neural Network (ANN) model locally. Once we are satisfied with our model, we will deploy it on AWS using SageMaker. 

This repository contains all the codes necessary to replicate the contents in <a href = "https://medium.com/@y.s.yoon/artificial-neural-network-ann-classifier-deployment-on-aws-cloud-servers-405254909161">this blog post</a>. If you have any comments or suggestions, email me at y.s.yoon@berkeley.edu.

# Part 1 - Build a Spam Classifier Locally

## Virtual Environment
Once we build a deep learning model using TensorFlow, we will deploy it on AWS using SageMaker. However, the version of SageMaker's TensorFlow is 1.15.5 at the time of this writing. This means that we have to use Python 3.7. For those of you who have Python 3.8 like me, it is important that we train the model using Python 3.7 in a virtual environment.

1. Type the following in Anaconda Prompt</br>
"conda create -n python37 python=3.7"


2. Activate the python37 virtual environment</br>
"conda activate python37"</br>
By the way, we can deactivate the virtual environment by typing "conda deactivate" but let's leave it active for now.


3. Install necessary packages in the environment. For TensorFlow, let's match the version with SageMaker's version.
pip install tensorflow==1.15.5
pip install pandas
pip install matplotlib


4. Make the environment available in Jupyter Notebook</br>
"pip install ipykernel"</br>
"ipython kernel install --user --name=python37"</br>

These will allow us to use the python37 kernel in Jupyter Notebook as shown below.

<img src ="https://github.com/youngdataspace/Build-and-Deploy-a-Spam-Detector-Model-on-AWS/blob/main/image_python37_kernel.JPG?raw=true">

## Build a Classifier Using Jupyter Notebook (spam_classifier.ipynb)
From the above image, click "python37" and create a new notebook using the virtual environment we just created.

Now we are ready to start working with data. Let's start writing in the spam_classifier.ipynb notebook. 

# Part 2 - Deploy the Trained Model on AWS Using SageMaker
## Preparation
#### Account
- Create an AWS account
- Sign in
#### Create an S3 bucket and upload the model
- Search S3 and go to Buckets
- Click the "create bucket" button in orange.
- Give it a name (e.g., spam-detector-s3) and select your region (I selected us-west-1)
- Click the name of the bucket to go into the bucket
- Upload "ann_model.zip" to the bucket
#### Create a Jupyter Notebook  
- Go to the SageMaker Dashboard by searching SageMaker.
- On the left menu, expand "notebook" and click instances.
- Click the "create notebook instance" button in orange.
- Give a name to the instance (I am calling it "spam-detector")
- The only other thing we need to set is "IAM role". Create one if you don't already have one.
- Leave all other settings as default and click the "create notebook instance" button in orange at the bottom.
- Click "Open Jupyter" to open Jupyter Notebook in SageMaker
- Create a new notebook by clicking "new" and selecting "conda_tensorflow_p36"

The remainder of this post will be explaining the deployment process in the notebook that we just created.

## Implementation of the Deployment Using SageMaker (deploy_spam_detector.ipynb)
