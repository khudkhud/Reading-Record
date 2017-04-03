Total:
## 1. Detection Recognition and Segment
#### 1.1 Face detection and recognition
##### [1] FaceNet: A Unified Embedding for Face Recognition and Clustering
**Keywords**

**FaceNet** 直接学习了从脸部图像到**欧式空间**的映射，使得面部的相似度直接可以用**距离**来表示
**128-bytes per face**

**Ideal Constraints**
$$
||f(x_i^a)-f(x_i^p)||_2^2 +\alpha < ||f(x_i^a)-f(x_i^n)||_2^2
$$
我们想要达到的目的，是所有的点与本类的距离和与异类的距离都至少差一个$\alpha$
$$
$$

**triplet loss function**
$$
L = \sum_i^N[||f(x_i^a)-f(x_i^p)||_2^2 - ||f(x_i^a)-f(x_i^n)||_2^2+\alpha]_+
$$
损失函数的定义说明，只在乎那些与本类的距离和与异类距离之差没能小于阈值$\alpha$的**不满足约束条件点***，而对那些已经满足条件的，则不予追究。这与SVM有些相似，关注边界附近的样本。追求的是尽可能所有的点都守约束，而不是总体的距离和最小之类的。

**Triplet Selection**
> In order to ensure faset convergence it is crucial to select triplets that violate the triplet constraint.也就是说，给定一个点，我们要找出与它最远的本类点，和与它最近的异类点。但是这样可能会导致不好的训练结果，因为质量差的人脸图片或错误的标签可能会主导选择的结果。
>We only compute the argmin and argmax with mini-batch. In our experiments we sample the training data such that around 40 faces are selected per identity per mini-batch.Additionally, randomly sampled negative faces are added to each mini-batch.
>Instead of picking the hardest positive, we use all anchor-positive pairs in a mini-batch while still selecting the hard negatives. We found the all anchor-positive method was more stable and converged slightly faster at the beginning of training.
>Selecting the hardest negtives can in practice lead to bad local minima early on in training, specially it can result in a collapsed model(i.e.$f(x)=0$). In order to mitigate this, it helps to select $
x_i^n$such that
$$
||f(x_i^a)-f(x_i^p)||_2^2 < ||f(x_i^a)-f(x_i^n)||_2^2
$$
We call these negative exemplars semi-hard, ad they are futher away from the anchor than the positive exemplar, but still hard because the squared distance is close to the anchor-positive distance. Those negative lie inside the margin $\alpha$

>we constrain this embedding to live on the d-dimensional hypersphere,i.e $||f(x)||_2=1$

#### 1.2 Person detection and identification
#### 1.3 General object detection
#### 1.4 Semantic Segment
## 2. Deep reinforcement learning
#### 2.1 Robotics
#### 2.2 Games
#### 2.3 General
## 3. Generative network
#### 3.1 GANs
#### 3.2 VAEs
## 4.Others
#####[3] Visualizing and Understanding Convolutional Networks
本文采用deconvolution的方法，研究了对于给定层激活的feature map,是原图中哪些部分的贡献。
>To examine a convnet, a deconvnet is attached to each of its layers, as illustrated in Fig. 1(top), providing a continuous path back to image pixels. To start, an input image is presented to the convnet and features computed throughout the layers. To examine a given convnet activation, we set all other activations in the layer to zero and pass the feature maps as input to the attached deconvnet layer. Then we successively (i) unpool, (ii) rectify and (iii) filter to reconstruct the activity in the layer beneath that gave rise to the chosen activation. This is then repeated until input pixel space is reached.

几点理解：
- 1）不是根据给出图像前向传播之后，采样的各层输出。而是给定一副图像，前向之后，对于某层的feature maps,根据deconvolution 网络，重构输入图像。
- 2）deconvolution 网络的输入，是原convolution网络的某层feature maps。此feature maps 是该层一个完整的feature maps,只是可以根据自己研究的需要，进行手工设定。比如想要看第一层的第一个feature map是原图哪部分激活的，可以设第一层一个feature map不变，其它置为0,然后通过deconvolution网络一直算到输入图像那一层。
- 3）因此，说卷积网络低层（接近原始图像的层）学到的低级边边角角的特征，高层学到的是高级组合特征。就是因为边边角角的特征就可以使低层feature map激活，而想要激活高层的feaure map，需要某些特定形状的图像。而如果只是看前向过程生成的feature maps的话，反而低层的图像更接近于原图，高层反而更抽象(所以看什么层学到什么特征，并不是单单根据前向过程中生成的feature maps来看的，之前一直有些混淆)。

## Waiting for Read