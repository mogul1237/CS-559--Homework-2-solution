# CS-559--Homework-2-solution

Download Here: [CS 559- Homework #2 solution](https://jarviscodinghub.com/assignment/cs-559-homework-2-solution/)

For Custom/Original Work email jarviscodinghub@gmail.com/whatsapp +1(541)423-7793

1. (30 pts) A neural network with the step activation function u(·) (i.e., u(x) = 1 if x ≥ 0 and u(x) = 0
if x < 0) and inputs (x, y) provides an output of 1 if (x, y) is a member of the shaded region. The network provides an output of 0 if (x, y) is not a member of the shaded region. Find the neural network (its topology and weights). Note that for the leftmost shaded region, as I have tried to show in the figure, the boundary points {(x, 0) : −2 ≤ x ≤ −1} ∪ {(−2, y) : −1 ≤ y ≤ 0} are excluded. -2 -1 2 1 1 x y -1 2. (70 pts) In this computer experiment, we will use the multicategory PTA for digit classification. Multicategory PTA is a simple extension of PTA and will be described in the following. (a) Read the contents of the webpage https://yann.lecun.com/exdb/mnist/ (b) There are 4 files listed in the beginning of the page as training set images, training set labels, test set images, and test set labels, download them. (c) Each image is 28×28, so that we will have a neural network 28×28 = 784 nodes in the input layer, and 10 nodes in the output layer. We will ignore the biases. We wish to find 784 × 10 = 7840 weights such that the network outputs [1 0 0 · · · 0]T if the input image corresponds to a 0, [0 1 0 · · · 0]T if the input image corresponds to a 1, and so on. (d) You will use the first n (n ≤ 60000) elements of training set images and training set labels to train our network via the multicategory perceptron training algorithm. Since the patterns are not linearly separable, the misclassification errors may not converge to 0 (unlike the last experiment in HW#1). You need to stop the iterations (epochs) when the ratio of misclassified input patterns falls below some threshold . The algorithm for this phase may thus be as follows: • 0) Given η, , n: • 1) Initialize W ∈ R 10×784 randomly. 1 • 2) Initialize epoch = 0. • 3) Initialize errors(epoch) = 0, for epoch = 0, 1, . . .. • 3.1) Do – 3.1.1) for i = 1 to n do (this loop is where we count the misclassification errors) ∗ 3.1.1.1) Calculate the induced local fields with the current training sample and weights: v = Wxi , where xi ∈ R 784×1 is the ith training sample (the vectorized version of the 28 × 28 image from the training set images). ∗ 3.1.1.2) The given input image may result in multiple 1s on different output neurons (or no 1s at all). For such scenarios, only for the purpose of calculating the misclassification errors, we choose the output neuron with the largest induced local field. In other words, we find the largest component of v = [v0 v1 · · · v9] T . Now, suppose that the largest component of v is vj , where j ∈ {0, . . . , 9}. Correspondingly, our network decides that the input image xi corresponds to the digit j. ∗ 3.1.1.3) If j is not the same as the input label (which is obtained from the training set labels), then errors(epoch) ← errors(epoch) + 1. – 3.1.2) epoch ← epoch + 1. – 3.1.3) for i = 1 to n do (this loop is where we update the weights) ∗ 3.1.3.1) W ← W + η(d(xi) − u(Wxi))x T i , where the step function u(·) is applied component-wise, and d(xi) ∈ R 10×1 is the desired output for training sample xi (which is obtained from the training set labels). For example, if the label for xi is 3, then d(xi) = [0 0 0 1 0 0 0 0 0 0]T . • 3.2) Loop to 3.1) if errors(epoch − 1)/n > .
(e) We now have some (hopefully) good weights that we have obtained via the multicategory PTA
above. We now test the corresponding network on the test set images and test set labels.
All we have to do is to use the loop 3.1.1) in the training algorithm:
• 0) Given W obtained from the multicategory PTA.
• 1) Initialize errors = 0.
• 2) for i = 1 to 10000 (note that there are 10000 test images)
– 2.1) Calculate the induced local fields with the current test sample and weights: v
0 =
Wx0
i
, where x
0
i ∈ R
784×1
is the ith test sample (the vectorized version of the 28 × 28
image from the test set images).
– 2.2) Find the largest component of v
0 = [v
0
0
v
0
1
· · · v
0
9
]
T
. Suppose that the largest component of v
0
is vj
0 , where j
0 ∈ {0, . . . , 9}.
– 2.3) If j
0
is not the same as the input label (which is obtained from the test set labels),
then errors ← errors + 1.
(f) Run Steps (d) and (e) for n = 50, η = 1, and some very small  ( = 0 should also work). You
should observe that step (d) terminates with 0 errors eventually. So, we have 0% error according to
our training samples. Plot the epoch number vs. the number of misclassification errors (including
epoch 0). Now, run Step (e) and record the percentage of misclassified test samples (over all
10000 test samples). Explain the discrepancy (if they are different why? if they are the same
why?) between the percentages of errors obtained through the training and test samples.
(g) Run Steps (d) and (e) for n = 1000, η = 1, and some very small  ( = 0 should also work).
Again, you should observe that step (d) terminates with 0 errors eventually. Repeat the same
tasks as in Step (f). Compare what you obtain here with what you have obtained in Step (f).
(h) Run Step (d) for n = 60000 and  = 0. Make note of (i.e., plot) the errors as the number of
epochs grow large, and note that the algorithm may not converge. Comment on the results.
(i) Using your observations in the previous step, pick some appropriate value for  (such that your
algorithm in (d) will eventually terminate). Repeat the following two subitems three times with
different initial weights and comment on the results:
• Run Step (d) for n = 60000, some η of your choice and the  you picked.
• Run Step (e) to with the W you obtained in the previous step.
