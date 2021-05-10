#### DO NOT PUSH ANY OF THE PRIVATE KEYS MENTIONED BELOW INTO THIS REPO
# Cancer Detection
This repository contains the server code. Below we describe the setup of our project. You can access this app here (if it is still being served by the team):

http://cd.wasaequreshi.com (or http://44.239.142.97)

### Tensor Server (classifier directory) (Not needed anymore. But keeping for reference on how to run your own Tensor Serving)
This directory contains the model which will be run using tensor_server. This is exported from the colab of our project:
```
MODEL_DIR = "/content/drive/My Drive/258 Project/export_model"
version = 1.0
export_path = os.path.join(MODEL_DIR, str(version))
print('export_path = {}\n'.format(export_path))

tf.keras.models.save_model(
    model,
    export_path,
    overwrite=True,
    include_optimizer=True,
    save_format=None,
    signatures=None,
    options=None
)
```
Whenever changes are made to the model, the export needs to be checked back into this repo with the latest changes. This model is then served with tensorflow server using the following command:

```
tensorflow_model_server --rest_api_port=8502 --model_name=saved_model --model_base_path=/home/ubuntu/cancer_classifier_app/classifier
```
### Flask Server (flask directory)
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

To learn more about screening, check this link out: 

```
https://medium.com/codebase/how-to-keep-multiple-linux-terminals-running-in-background-screen-ccf2e53b0d22
```

In addition if you want to do any git stuff on the server, run the following command:

```
eval `ssh-agent -s`
ssh-add ~/.ssh/github_march_4_2021
```
