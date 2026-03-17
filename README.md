# Developing a Neural Network Classification Model

## AIM

To develop a neural network classification model for the given dataset.

## Problem Statement

An automobile company has plans to enter new markets with their existing products. After intensive market research, they’ve decided that the behavior of the new market is similar to their existing market.

In their existing market, the sales team has classified all customers into 4 segments (A, B, C, D ). Then, they performed segmented outreach and communication for a different segment of customers. This strategy has work exceptionally well for them. They plan to use the same strategy for the new markets.

You are required to help the manager to predict the right group of the new customers.

## Neural Network Model

<img width="980" height="708" alt="image" src="https://github.com/user-attachments/assets/54ddd87d-ac58-4510-92a8-1d6f85f5aa1b" />


Include the neural network model diagram.

## DESIGN STEPS

### STEP 1:
Import necessary libraries and load the dataset.

### STEP 2:
Encode categorical variables and normalize numerical features.

### STEP 3:
Split the dataset into training and testing subsets.
### STEP 4:
Design a multi-layer neural network with appropriate activation functions.
### STEP 5:
Train the model using an optimizer and loss function.
### STEP 6:
Evaluate the model and generate a confusion matrix.
### STEP 7:
Use the trained model to classify new data samples.
### STEP 8:
Display the confusion matrix, classification report, and predictions.


## PROGRAM

### Name: DEEPIKA R
### Register Number:212224040061

```
class PeopleClassifier(nn.Module):
    def __init__(self, input_size):
        super(PeopleClassifier, self).__init__()
        #Include your code here
        self.fc1=nn.Linear(input_size, 32)
        self.fc2=nn.Linear(32, 16)
        self.fc3=nn.Linear(16, 8)
        self.fc4=nn.Linear(8, 4)
    def forward(self, x):
      #Include your code here
      x=F.relu(self.fc1(x))
      x=F.relu(self.fc2(x))
      x=F.relu(self.fc3(x))
      x=self.fc4(x)
      return x


```
```
def train_model(model, train_loader, criterion, optimizer, epochs):
  #Include your code here
  for epoch in range(epochs):
    for inputs, labels in train_loader:
      optimizer.zero_grad()
      outputs=model(inputs)
      loss=criterion(outputs, labels)
      loss.backward()
      optimizer.step()
    if (epoch + 1) % 10 == 0:
        print(f'Epoch [{epoch+1}/{epochs}], Loss: {loss.item():.4f}')

```
```
model = PeopleClassifier(input_size=X_train.shape[1])
criterion =nn.CrossEntropyLoss()
optimizer =optim.Adam(model.parameters(),lr=0.001)


train_model(model,train_loader,criterion,optimizer,epochs=100)
```



## Dataset Information
<img width="1190" height="729" alt="image" src="https://github.com/user-attachments/assets/22a5601e-d3ea-4d03-833e-4e2c55a41f3e" />



## OUTPUT
### Confusion Matrix
<img width="846" height="591" alt="image" src="https://github.com/user-attachments/assets/704b219e-3912-48a6-9226-88d7a6fb0698" />








### Classification Report
<img width="760" height="423" alt="image" src="https://github.com/user-attachments/assets/afc7f09c-d143-4f84-b3cb-656806d884b6" />





### New Sample Data Prediction
<img width="977" height="366" alt="image" src="https://github.com/user-attachments/assets/9474b126-b206-4b74-a9c1-d6a7f5166b2b" />




### Result
Thus the neural network classification model was successfully developed.
