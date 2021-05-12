#  Breast Cancer Diagnosis Using Deep Transfer Learning
CMPE 258 Deep Learning Project : Breast Cancer Diagnosis Using Deep Transfer Learning
## Demo Information

You can view the demo of our project here: https://drive.google.com/file/d/1Pi0PpHzcglJdjgp4axyIvtRlRUiqe4is/view

In addition we have checked the video into the repo: https://github.com/s-c-soma/cmpe297_BreastCancerDiagnosis_withDeepTransferLearning/blob/main/deliverables/final_project_demo.mp4

## Setup
To run latest colab, please do the following
1. Setup Kaggle API
Steps to have kaggle API working in colab are listed here
https://towardsdatascience.com/setting-up-kaggle-in-google-colab-ebb281b61463

2. Enter your token in 1.1. 

3. After youve entered your token once run cells under 1.0 once. Then so long as you dont terminate your session, even if gets killed/crashes,
next time you dont need to run cells under 1.0 again. You start from 2.0. However, if you terminate your session, you will need to repeat running 1.0.

## ML-OPS E2E Pipeline Setup: Kubeflow Setup for Cancer Classification

**kubeflow** folder contains all the necessary code needed to create, update and deploy a pipeline to kubeflow. Please use the template.ipynb file as a reference on how to execute these commands. This notebook must exist on a Jupyter notebook on GCP.

## WEB App: Flask Setup for Cancer Classification
**flask** folder contains all the flask server code. Below we describe the setup of our project. You can access this app here (if it is still being served by the team):

http://cd.wasaequreshi.com (or http://44.239.142.97)

This contains the code for the UI and the backend which interacts with AI Platform on GCP. The UI allows the user to input a image. The backend will then make a request with the input file to the model on AI Platform for a prediction and display the output back on the screen respectively.

Run the following command to serve this app:

```
sudo python3 main.py
```

### EC2
This app code is served on a single EC2 instance. To access this EC2, use the private key shared by the admin and run the following command:

```
ssh -i ~/Desktop/258_key.pem  ubuntu@44.239.142.97
```

I have created a screen for the app code. Once you ssh, you can view them by running the following:

```
screen -ls

For example:

ubuntu@ip-172-31-3-162:~/cancer_classifier_app/classifier/1$ screen -ls
There are screens on:
	39220.flask_server	(04/13/21 21:00:34)	(Detached)
1 Sockets in /run/screen/S-ubuntu.
```

You can see the flask_server running in the background.

In addition if you want to do any git stuff on the server, run the following command:

```
eval `ssh-agent -s`
ssh-add ~/.ssh/github_march_4_2021
```
