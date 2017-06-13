# dlnf_project1_bikeshare_ann

-------------- Submission 3 Comments -------------
Everything should be working fine now

-------------- Submission 2 Comments -------------
I have made changes to the neural net & hyperparameters, all of which pass the unit tests. I have decided to maintain the usage of the sigmoid prime function as allows me to compare with the forward pass more clearly. Somehow, the epochs seems to lag my kernel so much, that it is unable to load the training & validation loss graphs [*] - hence I am unable to effectively choose my hyperparameters. I am pretty annoyed and have been trying many times on all browsers. Any idea why this is happening? Much Appreciated.

Feedback:

You only printed Training loss and Validation loss 5 times up until 0.1% of progress but you need to print up until 99.9% or 100% progress. The reason is you are printing all the arrays to the Notebook cells which slows down your training significantly. Please remove all your print statements from the def train(self, features, targets): function. Then retrain your network making sure that all the cells run including the last one where your can see the loss plot.

-------------- Submission 1 Comments -------------
There seems to be an attribute error with the code for the pre-assigned hyperparameter tuning, which has inhibited me from selecting the correct variables, please let me know when it is fixed and I'll be happy to re-submit that portion. Thanks!

Feedback:

1) Replace these lines:

            hidden_outputs = np.reshape(hidden_outputs,[2,1])
            delta_weights_h_o += output_error_term * hidden_outputs # 1:1 * 1:2
            
with delta_weights_h_o += output_error_term * hidden_outputs[:, None]

2) You are doing redundant calculations with self.activation_function_prime(hidden_inputs). You could have used hidden_outputs * (1 - hidden_outputs) since you have already calculated hidden_outputs = self.activation_function(hidden_inputs)

The number of epochs is chosen such the network is trained well enough to accurately make predictions but is not overfitting to the training data.Redo this after fixing you NN.

The way to judge if the number of epochs is too high is by taking a look at validation loss graph. If it start to increase again, then it means the neural network starts to overfit.
On the other side, if the validation loss is still decreasing right until the end, it means that you have ended the training too early, and the number of epochs is too low.Most students used 1000-10000 epochs.

The number of hidden units is chosen such that the network is able to accurately predict the number of bike riders, is able to generalize, and is not overfitting.
4 hidden units is too low. I suggest you use at least 10. If the number of hidden units is too low, then neural network will not be able to generalize well.

In general, as a rule of thumb you can start to experiment with the number of units equal to the mean of the number of units in the neighboring layers. So in this project with 56 input units and 1 output unit, you could have started with something around 25.
For more information you can read this resource: https://www.quora.com/How-do-I-decide-the-number-of-nodes-in-a-hidden-layer-of-a-neural-network

The learning rate is chosen such that the network successfully converges, but is still time efficient.
Try higher values too. If you select too low LR, the training will take too long.
