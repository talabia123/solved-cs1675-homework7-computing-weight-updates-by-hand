Download Link: https://assignmentchef.com/product/solved-cs1675-homework7-computing-weight-updates-by-hand
<br>
<u>Part I: Computing weight updates by hand</u>

In recitation, we show how to compute activations in a neural network, and how to perform stochastic gradient descent to train it. We compute activations for two example networks, but only show how to train one of them. Show how to train the second network using just a single example, <span style="font-family: courier new;">x = [1 1], y = [0 0]</span> (note that in this case, the label is a vector). Initialize all weights to 0.05. <span style="color: red;">Use a learning rate of 0.3.</span> Include your answers in text form in a file <span style="font-family: courier new;">report.pdf/docx</span>.

<u>Part II: Training a neural network</u>

In this exercise, you will write code to train and evaluate a very simple neural network. We will follow the example in Bishop that uses a single hidden layer, a tanh function at the hidden layer and an identity function at the output layer, and a squared error loss. The network will have 30 hidden neurons (i.e. M=30) and 1 output neuron (i.e. K=1). To implement it, follow the equations in the slides and your textbook.

First, write a <span style="font-family: courier new;">function [y_pred, Z] = forward(X, W1, W2)</span> that computes activations from the front towards the back of the network, using fixed input features and weights. Also use the forward pass function to evaluate your network after training.

<b>Inputs:</b>

<ul>

 <li>an NxD matrix <span style="font-family: courier new;">X</span> of features, where N is the number of samples and D is the number of feature dimensions,</li>

 <li>an MxD matrix <span style="font-family: courier new;">W1</span> of weights between the first and second layer of the network, where M is the number of hidden neurons, and</li>

 <li>an 1xM matrix <span style="font-family: courier new;">W2</span> of weights between the second and third layer of the network, where there is a single neuron at the output layer</li>

</ul>

<b>Outputs:</b>

<ul>

 <li>[5 pts] an Nx1 vector <span style="font-family: courier new;">y_pred</span> containing the outputs at the last layer for all N samples, and</li>

 <li>[5 pts] an NxM matrix <span style="font-family: courier new;">Z</span> containing the activations for all M hidden neurons of all N samples.</li>

</ul>

Second, write a <span style="font-family: courier new;">function [W1, W2, error_over_time] = backward(X, y, M, iters, eta)</span> that performs training using backpropagation (and calls the activation computation function as it iterates). Construct the network in this function, i.e. create the weight matrices and initialize the weights to small random numbers, then iterate: pick a training sample, compute the error at the output, then backpropagate to the hidden layer, and update the weights with the resulting error.

<b>Inputs:</b>

<ul>

 <li>an NxD matrix <span style="font-family: courier new;">X</span> of features, where N is the number of samples and D is the number of feature dimensions,</li>

 <li>an Nx1 vector <span style="font-family: courier new;">y</span> containing the ground-truth labels for the N samples,</li>

 <li>a scalar <span style="font-family: courier new;">M</span> containing the number of hidden <span style="color: red;">neurons</span> to use,</li>

 <li>a scalar <span style="font-family: courier new;">iters</span> defining how many iterations to run (one sample used in each), and</li>

 <li>a scalar <span style="font-family: courier new;">eta</span> defining the learning rate to use.</li>

</ul>

<b>Outputs:</b>

<ul>

 <li>[10 pts] <span style="font-family: courier new;">W1</span> and <span style="font-family: courier new;">W2</span>, defined as above for <span style="font-family: courier new;">forward</span>, and</li>

 <li>[5 pts] an <span style="font-family: courier new;">iters</span>x1 vector <span style="font-family: courier new;">error_over_time</span> that contains the error on the sample used in each iteration.</li>

</ul>

<u>Part III: Testing your neural network on wine quality</u> (15 points)

We will use the Wine Quality dataset from HW3 to test the neural network implementation. Write your code in a script <span style="font-family: courier new;">neural_net.m</span>.

<ol>

 <li>[2 pts] Load the wine dataset, define the train/test split as in HW3, and set the number of hidden units, the number of iterations to run, and the learning rate.</li>

 <li>[3 pts] Call the <span style="font-family: courier new;">backward</span> function to construct and train the network. Use 1000 iterations and 30 hidden neurons.</li>

 <li>[5 pts] Then call the <span style="font-family: courier new;">forward</span> function to make predictions and compute the root mean squared error between predicted and ground-truth labels, <span style="font-family: courier new;">sqrt(mean((y_test_pred – y_test).^2))</span>. Report this number in a file <span style="font-family: courier new;">report.pdf/docx</span></li>

 <li>[5 pts] Experiment with three different values of the learning rate. For each, plot the error over time (output by <span style="font-family: courier new;">backward</span> above). Include these plots in your report. My plot looks like this:<img decoding="async" width="500/" data-src="./CS1675_ Homework 7_files/mse_plot.png" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

  <noscript>

   <img decoding="async" src="./CS1675_ Homework 7_files/mse_plot.png" width="500/">

  </noscript></li>

</ol>

<b>Submission:</b> Please include the following files:

<ul>

 <li><span style="font-family: courier new;">report.pdf/docx</span></li>

 <li><span style="font-family: courier new;">forward.m</span></li>

 <li><span style="font-family: courier new;">backward.m</span></li>

 <li><span style="font-family: courier new;">neural_net.m</span></li>

</ul>