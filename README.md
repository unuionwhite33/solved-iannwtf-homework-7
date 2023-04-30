Download Link: https://assignmentchef.com/product/solved-iannwtf-homework-7
<br>
<h1>1      Data set</h1>

This week we will work with the fashion mnist dataset. It contains 60000 images 28x28x1 which are labeled into 10 different categories. You can load the dataset from the tf.keras.dataset module.

Perform necessary or beneficial preprocessing steps.<sup>1</sup>

<h1>2      Model</h1>

Implement a convolutional autoencoder (and a variational autoencoder for an outstanding).

2.1 Convolutional Autoencoder • The Autoencoder should consist of an encoder and a decoder, which can be called independently. <sup>2</sup>

<ul>

 <li>Encoder: The encoder should reduce the size of featuremaps like a CNN.<sup>34 </sup>At the end of the encoder, flatten the feature maps and use a dense layer to produce an embedding of a certain size. <sup>5</sup></li>

 <li>Decoder: The decoder takes the embedding from the encoder as input. Use a dense layer to restore the dimensionality of the flattened feature maps from the encoder and reshape the resulting vector into feature maps again. Use upsampling or transposed convolutions to mirror your encoder. As an output layer use a convolutional layer with one filter and sigmoid activation to produce an output image.</li>

</ul>

<h2>2.2      (Variational Autoencoder)</h2>

For the implementation of a Variational Autoencoder refer to online sources. There are good tutorials that do a better job at explaining the implementation than we can do in a few lines of text here. There are also different ways to implement VAEs in tensorflow. Here is a <a href="https://www.tensorflow.org/tutorials/generative/cvae">guide</a> using only tensorflow. There is also the <a href="https://www.tensorflow.org/probability">tensorflow probability</a> library, which provides probabilistic layers. Have a look at <a href="https://blog.tensorflow.org/2019/03/variational-autoencoders-with.html">this tutorial</a><a href="https://blog.tensorflow.org/2019/03/variational-autoencoders-with.html">,</a> which explains how to build VAEs with tfp. You can also use any other source that you can dig up. Please explain in detail how sampling and the loss are handled in your implementation so we know you did not just copy and paste without understanding whats going on. If you run into troubles in this part, still feel free to come to the coding class.

<h1>3      Training</h1>

Then train your network(s). Autoencoders learn unsupervised and do not use the labels. Compute the loss between the input image and the reconstructed image. While training it is nice to plot some example images from the test set with their reconstructed counterparts to visualize the training progress. <sup>6</sup>

<h1>4      Latent Space Analysis</h1>

Embed the first 1000 images of the test set using the encoder. Reduce the dimensionality of the embeddings to two using the t-SNE algorithm.<sup>7 </sup>Then plot the data points, colored according to their class. Evaluate the result. Is it what you expected? How is this related to the courseware content? Further interpolate linearly between the embeddings of two images and plot the reconstructed images. Again relate this to the courseware content. For the Variational Autoencoder part do the same and compare the results.

<h1>5      Outstanding Requirements</h1>

<strong>General Reminder: </strong>Rating yourself as outstanding means that your code could be used as a sample solution for other students. This implies not relying on or thoroughly explaining things not covered in the lecture so far and providing clean understandable code and explanatory comments when necessary.

This week the main part of the outstanding distinction is to implement a Variational Autoencoder in addition and to compare the analysis to the standard Autoencoder.

The following points are still required but you should be able to copy and paste most of it by now.

<ul>

 <li>A proper Data Pipeline (that clearly and understandably performs necessary preprocessing steps and leaves out unnecessary pre-processing steps).</li>

 <li>Clean understandable implementations of your data set.</li>

 <li>Commments that would help fellow students understand what your code does and why. (There is no exact right way to do this, just try to be empathic and imagine you’re explaining topic of this week to someone who doesn’t now much about it.) Nice visualizations of the losses and accuracies. (You don’t have to plot every epoch. Once in the end is enough. Although some print statements to keep track of the performance during training are welcome.)</li>

</ul>

<h1>Notes</h1>

1 Relevant preprocessing steps:

<ul>

 <li>Shuffling Normalize the images to the range (0,1). Then you can use the sigmoid activation as output to reconstruct images in the same range</li>

 <li>Batching, an orientation would be minibatches of size 64.</li>

</ul>

2

The easiest way to do this is with model subclassing. Define separate models for the encoder and decoder and initialize them in the autoencoder constructor.

3 You can either use convolutional layers with stride 2 for subsampling or convolutional layers with stride 1 followed by a pooling layer

4

subsampling two times i.e. to a size of 7×7 should be enough

5

As a rule of thumb, the smaller the embedding, the harder the training and the more layers required. If experimentation fails you, try 10.

6 Training Hyperparameters for orientation:

<ul>

 <li>epochs: around 10</li>

 <li>Try something around 0.001</li>

 <li>optimizer: Adam</li>

</ul>

7 t-SNE is a dimensionality reduction algorithm particularly suited for visualization. You don’t have to implement it yourself, you can use an existing library, e.g. <a href="https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html">https://scikit-learn.org/stable/ </a><a href="https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html">modules/generated/sklearn.manifold.TSNE.html</a><a href="https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html">.</a>

If you want to know how it works have a look at <a href="https://towardsdatascience.com/t-sne-clearly-explained-d84c537f53a">this blogpost</a><a href="https://towardsdatascience.com/t-sne-clearly-explained-d84c537f53a">.</a> For some guidance on what can be and what can not be interpreted from the results refer to <a href="https://distill.pub/2016/misread-tsne/">this Distill article</a>