# Federated-Learning #

## Federated Learning on FMNIST Dataset ##

- **Dataset** : 
The Fashion MNIST Dataset contains 70,000 images which include 60,000 training images and 10,000 testing images. Each example is a 28x28 grayscale image which is associated with 10 different classes. This dataset is divided into 6 training batches and 1 test batch. The batch size is 10,000.

- **Execution Process** : 
For the execution of image classification of Fashion MNIST data using Federated Learning, we have used two approaches first manually dividing the data and modelling  and other using Pysyft hooked with Pytorch.

  - **Manual Process** : 
  The data is first divided into six clients, having 10,000 training images each. The images are normalized. Thereafter we instantiated the client models. For every client, the test images are common (10,000). For this we have used Adam optimizer and Sparse Categorical Cross Entropy as a loss function. Next we train our client models and extract out the test accuracy for each client. Next we use the federated learning for training our client models for 50 communication rounds. Here we extracted the weights of each model and assigned the mean average of the weights to every model and train again. Thereafter we have trained without using federated learning and record the results.
  
   Following are the results before updating the parameters:
  
  | Clients  | Training Accuracy On Individual Data(in %) |  Testing Accuracy on Individual Data(in %) |
  | ------------- | ------------- | ------------ |
  | Client1  | 78.18  | 81.84 |
  | Client2  | 77.75  | 80.75 |
  | Client3  | 77.93  | 81.7 |
  | Client4  | 78.75  | 79.11 |
  | Client5  | 78.15  | 78.86 |
  | Client2  | 77.12  | 80.52 |
  
  We have found that the accuracy of the model which was trained using federated learning gives accuracy 87.40% while without federated learning the accuracy is around 84%. So federated learning not only provides privacy but also gives more accurate results in a fast manner.

  - **Using Pysyft and Pytorch** : 
  Initially we hook Pytorch with Pysyft that adds extra functionalities to support Federated Learning. We created six imaginary clients using syft. Thereafter we define the batch size, test batch size, learning rate etc. We load the data and convert it into a federated dataset which is then used to iterate over our remote batches during training loops. We send the data to the remote clients and use local Pytorch to perform the operations remotely. We have used SGD optimizer. The test function remains the same as it is run locally on our machine only whereas training happens remotely. We start training the global model using the same code which is used for training the local model. The Accuracy we got was 89%.
  
  
Refer [Federated Learning with Google](https://federated.withgoogle.com/) for moree... :book:
