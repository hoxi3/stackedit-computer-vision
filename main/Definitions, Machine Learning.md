affordance
: an obect's affordances are how a human may interact with it

AMT (Amazon Mechanical Turk)
: web service to get humans to perform simple tasks for cheap

AP (average precision)
: At given IoU threshold(s), calculate precision and recall.

Attention mechanism *[cf.](https://arxiv.org/pdf/1808.03728.pdf)*
: Given a query $q \in R^{d_k}$ and an input sequence (of n words) $K = [k_1,...k_n] \in R^{d_k \times n}$. A compatibility function $f(k_i, q)$ computes a relativity score between the query $q$ and each word $k_i$. Then apply the softmax function to these scores to define a categorical distribution $p(i|K,q)$. Then the output is the weighted sum of the inputs $out = \sum^n_{i=1} p(i|K,q)k_i$
If the keys and values are distinct entities, then the attention function would be $f(q,k,v)$
The *Scaled Dot-product Attention Mechanism* is defined as $f(q, k_i) = \frac{<k_i,q>}{\sqrt{d_k}}$
There are 3 types: (1) soft, (2) hard, (3) local
- **Soft attention** mechanism - takes into account all words in the sequence, regardless of type. Easy but expensive and less accurate.
- **Hard attention** mechanism - locates accurately to only one key $k_{i_o}$. Uses reinforcement learning because the choice of key makes it not differentiable.
- **Self attention** mechanism - the query and the key are the same, i.e. $q$ comes from $K$. We are able to learn the relatedness of different parts of the input sequence, no matter their distance.
- **Multi-head attention**
- **Multi-level attention**: Apply the attention function multiple times. At the first level, $f(q,k,k)$ gives you attention in the dimension of the keys. Treat that output as a query for the next application of the function: $f(f(q, k, k), k, v)$ gives you attention in the dimension of the values. 

Batch Normalization [[src](https://arxiv.org/pdf/1502.03167.pdf)]
: In training, at every layer, compute a mean and stdev for each feature/channel using the entire batch (every location, every image). Normalize said layer's output on a feature-by-feature basis. Make a running avg and running stdev for the whole training set to use as mean and stdev during testing. When the batch is too small, use **Group Normalization** .

 Beam Search
 : Non-greedy selection for output from a sequence (as RNN). At each time-step, it chooses the $K$ most likely hypotheses $y_2$ based on $p(y_1) \times p(y_2|y_1) \times ...$. Keep extending $K$ rays (keeping the top $K$ at each timestep) until end of sequence is reached on all rays. Then output the sequence with the highest joint distribution $p(y_1, y_2, ...)$

CAM (Class Activation Map)
: work backward to show what part of input image is contributing to classification under class *C*

CorLoc (correct localization)
: metric used in object detection	

CRF (Conditional Random Fields)
: (see last paragraph of 4.1 of [Detecting Visual Relationships with Deep Relational Networks](http://openaccess.thecvf.com/content_cvpr_2017/papers/Dai_Detecting_Visual_Relationships_CVPR_2017_paper.pdf))

Distillation
: Transferring knowledge from a more complex network to a smaller one by feeding an input into both and letting the label for the smaller network be the output of the larger one.

Entropy
: $H(p) = E[I(X)] = E[-log(P(X)] = \sum_{i=1}^n P(x_i)I(x_i)$
$= -\sum_{i=1}^n P(x_i)log(P(x_i))$
$H$ is entropy
$E$ is expectation (average)
$X$ is a random variable
$I$ is the information content of $X$

FiLM (Feature-wise Linear Modulation)
: ?

Fully supervised learning
: *see "Supervised learning: fully supervised"*

**GAN  (Generative Adversarial Network)** [[src](https://arxiv.org/abs/1406.2661)] [[CS231N](http://vision6.idav.ucdavis.edu:8888/notebooks/GANs-PyTorch.ipynb)] [[Hacks](https://github.com/soumith/ganhacks)]

GCN (Graph Convolutional Network)
: The input is effectively neighborhood of graph nodes. For layer $(l+1)$ and node $i$, the input is the output of the previous layer plus a sum of linearly transformed neighbours (at the same layer):
$z_i^{(l+1)} = \sigma( z_i^{(l)} + \sum_{j \in N(i)} Wz_j^{(l)})$
(Attention weights $\alpha_j$ can be applied to $Wz_j^{(l)}$ for [aGCN](https://arxiv.org/pdf/1808.00191.pdf).)

GMM (Gaussian Mixture Model)
: Assumes data points are generated from a mixture of a finite number of Gaussians. It's basically a k-means model with the inclusion of covariance information.

GNN (Graph  Neural Networks)
: "An iterative process, which propagates the node states until equilibrium; followed by a neural network." [[cite](https://openreview.net/pdf?id=rJXMpikCZ)]

Group Normalization
: When the minibatch is too small for batch normalization to be effective, compute a mean and standard deviation for each image (all pixels, all channels). Use these statistics to normalize the minibatch. **Synchronized batch normalization** is used when the batch is actually spread across multiple processors; the mean and stdev are therefore also spread across multiple processors.

Hard negative examples
: negative examples that are currently rated as positive or ambiguous by the detector (see also 'hard-negative mining)

Hard-negative mining
: Identifying training set examples (or portions thereof) which are given low probabilities by the model, but which should be high probability instead. [cite](https://arxiv.org/pdf/1312.6199.pdf)

HOG (Histogram of Oriented Gradients) [[tuorial](http://mccormickml.com/2013/05/09/hog-person-detector-tutorial/)][[tutorial](https://lilianweng.github.io/lil-log/2017/10/29/object-recognition-for-dummies-part-1.html)]
: Used for object detection. The entire object is represented by a single feature vector, as opposed to many feature vectors representing smaller parts of the object. The HOG person detector uses a sliding detection window which is moved around the image. At each position of the detector window, a HOG descriptor is computed for the detection window. This descriptor is then shown to the trained SVM, which classifies it as either “person” or “not a person”.
: To recognize persons at different scales, the image is subsampled to multiple sizes. Each of these subsampled images is searched.

Homography
: An 8-d metric for similarity between images. It assumes only rotational change from the obeserver's POV (no translation).

HOOF (Histogram of Oriented Optical Flow)
: ?

Image Pyramid
: Perhaps means upsampling to test a single image at multiple scales. (See [SNIP](https://www.cs.umd.edu/~bharat/snip.pdf))

Inception model
: perform multiple parallel filter operations (e.g. 1x1, 3x3, 5x5, 3x3 max pooling) and concatenate the results of all to be input for the next layer. See [GoogLeNet](https://arxiv.org/pdf/1409.4842.pdf).

Inter-attention
: *see Self-attention*

Layer Normalization
: In training and testing, at every layer, compute a mean and stdev for each image using the whole feature vector (every feature map). Normalize said image's output on an image-by-image basis.

**[Loss Functions](https://isaacchanghau.github.io/post/loss_functions/)**
 - **Contrastive Loss** - Used in Siamese networs, a distance-based loss (as opposed to prediction error-based loss). It tries to ensure that similar examples are embedded close together while non-neighbours are pushed apart.
 - **Cross Entropy Loss** - Used with Softmax classifier. Implemented as $1 - p$ where $p$ is the predicted probability of the target class.
 - **Focal Loss** - To overcome the class imbalance problem of cross entropy loss (wherein the easy-to-classify examples dominate the gradient). $L(p) = -(1-p)^\gamma log(p)$. Thus, hard-to-classify examples get more weight. $\gamma$ is a tunable parameter.
 - **Hinge Loss** - a.k.a. Max margin loss. Used with SVM classifier.
 - **Mean Squared Error (MSE)** - Used in linear regression. The method of minimizing with MSE is Ordinary Least Squares.
 - **Ranking Loss** - The likelihood of class `k` for the input, minus the likelihood of the most likely non-`k` class.
- **Triplet Loss** - The distance between objects A and B should be less than the distance between objects A and C.

LSTM (Long Short Term Memory)
: One sort of memory cell for implementing RNN's. The motivation is to avoid the vanishing/exploding gradients of vanilla RNN's.
: It has hidden state $h$ and state $c$.  It has gates $i$ $f$ $o$ $g$.
: To make the LSTM bidirectional, use 2 LSTM's, and process the input sequence in opposite directions. Concatenate their $c$'s.

mAP (mean Average Precision)
: When given without a fraction (no "@"), it is the average of {@.5,@.55,@.6,...,@.95}.

Message passing
: Features get concatenated from different branches of the network

MLP (multi-layer perceptron)
: vanilla feed-forward neural network. Still needs some 'activation' function such as ReLU to provide non-linearity.

Mode collapse
: is when the generator generates a limited diversity of samples, or even the same sample, regardless of the input.

Multi-instance learning (MIL)
: Given a bag of instances, you know that one of them corresponds to the label, but you don't know which one. One way to proceed is to run your model on all of them and then backpropagate on only the instance which produced the lowest error.

NMS (non-maximum suppression)
: used to choose among overlapping bounding boxes.

Network-in-Network
: proposed by Min Lin, Qiang Chen, and Shuicheng Yan. Network in network. CoRR, abs/1312.4400, 2013. In vision, 1x1 conv layers followed by relu.

Optical flow
: A 2xHxW tensor holding the $x$ translation and $y$ translation of every pixel in transition between two similar images.

Partially supervised learning
: *see "Supervised learning: partially supervised"*

Perplexity
: $2^{H(p)}$ where $H$ is entropy of a probability distribution $p$
I.e. $2^{-\sum_x p(x) log(p(x))}$
For a model $q$ fir an unknown probability distribution $p$, the perplexity would be $2^{-\frac{1}{N}\sum_{i=1}^N{log( q(x_i) )}}$

Recall @ X (Recall@X, R@X)
: Among the top $X$ predictions across a dataset (sorted, for example, by confidence), the fraction of correct predictions. "Recall @ x computes the fraction of times the correct relationship is predicted in the top x confident relationship predictions."
"Rec@N computes the ratio of the correct relationship instance that is covered in the top N predictions per image." [src](https://arxiv.org/pdf/1807.04979.pdf)

ROI Pooling
: An ROI can be any size, but the network that operates on it expects a particular size. ROI Pooling changes the size of the ROI to fit the following network. First proposed in [Fast R-CNN](https://deepsense.ai/wp-content/uploads/2017/02/1504.08083.pdf). [[Brief explanation](https://deepsense.ai/region-of-interest-pooling-explained/)]

RPN (Region Proposal Network)
: propounded by R-CNN? Used in localization or object recognition to look for bounding boxes.

Selective search [[tutorial](https://lilianweng.github.io/lil-log/2017/10/29/object-recognition-for-dummies-part-1.html)]
: A non-neuromorphic algorithm for generating region proposals for object detection. Apply Felzenszwalb and Huttenlocher’s graph-based image segmentation algorithm. Then merge regions based on similarity. All regions (initial and results of merge) become proposals for object detections.

Self-attention
: When an attention mechanism us used to compute a representation of a single sequence.

SIFT [[paper](http://www.cs.ubc.ca/~lowe/papers/iccv99.pdf)]
: Algorithm for object recognition...

Sketch token
: a tight distribution of contours passing through the center of an image patch

SLAM (Simultaneous Localization and Mapping) [[wiki](https://en.wikipedia.org/wiki/Simultaneous_localization_and_mapping)]
: The computational problem of constructing or updating a map of an unknown environment while simultaneously keeping track of an agent's location within it.

Spatial Pyramid Pooling (SPP)
: ?

Spectral clustering
: clustering where the eigenvalues of the similarity matrix of the data are used to perform dimensionality reduction

Supervised learning
:  - **fully supervised** - you know all the ground truth information (for training)
    - **partially supervised** - see *semi-supervised*
    - **self-supervised** - makes use of non-visual information, intrinsically correlated to the data (domain knowledge)
    - **semi-supervised** - for some of the training data, you know all the ground truth, but for some of the data you don't have all the ground truth (e.g. you know bounding box *and* segmentation for some data but know only bound box for the remaining data). So you train on the fully-labelled data, make predictions on the unlabelled data, then retrain on the whole set (using your predictions as labels).
    - **weakly supervised** - you know one thing and want to predict other (e.g. you know bounding box and want to predict mask)

Surface Normal
: For each pixel in an image, the ray extending perpendicular from the surface represented by the pixel.

Variational Autoencoder (VAE)
: Generative model. Easier to train (more stable) than GAN, but good GAN yields better results. Codiscovered: [1](https://arxiv.org/abs/1312.6114), [2](https://arxiv.org/abs/1401.4082)

Wasserstein Distance
: A distance between two probability distributions, aka "the earth-mover's distance."

Weakly supervised learning
: *see "Supervised learning: weakly supervised"*
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUzNDAxNDgyLC0xMDEzOTgyMzIzLDIwMT
E0MzU4ODMsLTQwMjgyNjQ0NywxNDU4NzE2OTkyLDE4NDIxOTE4
MTgsLTIxMDEwMjQwNDAsLTkzMzIxMzk4NSwtMTIyMzAzMjUzNS
wxNTA0ODYwMjI4LDE0NTE4MzM0NTcsLTE2MzY2NDA0MTksLTEz
ODc5NDIxNjcsLTg1NDI3OTAwNyw5MTc2OTEyNjEsLTE4MTkwND
AzNTAsNTE5MTA3OTUzLDc1OTc4ODEyMSw0MjcxMTg3NjZdfQ==

-->