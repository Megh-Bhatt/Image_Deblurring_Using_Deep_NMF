# Image_Deblurring_Using_Deep_NMF

Deep NMF uses a multi-layer approach where the factorization occurs in several layers,
similar to deep learning models. Instead of directly factorizing V into W and H, we
decompose V through intermediate layers of factorization:
#### V ≈ W1 · W2 · · · · · Wk · H

Here, each Wi represents a layer of decomposition, and the deeper structure allows for
capturing more complex representations of the data.

### Methodology

So the first task was to find the way to implement the model/code, and after reading
some text we found that AutoEncoder is the thing we are looking for. Now, as we are
dealing with images liner autoencoders are not a good fit. hence we used ConvAutoen-
coders.
Now, the Next step was to find a good dataset to train the model. After searching a
lot we found a dataset on Kaggle which we thought is perfect. It had over 2500 images of
160*160 pixels. then we used Gaussian blur to create blur images with a kernel size of 20
and sigma=3.
Now we have everything we need hence, we can start building our model and set its
parameters. the model has 5 Convolutional Layers of kernel size 3 and stride = 2 pooling
layers were not used as the task of downsampling was done while feature extraction it self.
now we cant take more than 5 layers because we have images of size 160*160 and each
layer downsamples it by half hence there not much feature length left after final layer.
The model was trained with batch size of 64 with activation function being ReLU and
optimizer Adam. the loss function was made with two losses MSE loss and siem loss, siem
loss was used to help model take bold decision and increase its entropy to search for better
solution.

#### loss = MseLoss + SiemLoss ∗ 0.1
