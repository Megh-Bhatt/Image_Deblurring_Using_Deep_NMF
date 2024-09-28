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

The model was trained for 100 epoch on T4 Gpu available on kaggle, various experi-
ments were made with loss functions and layer parameters but the best output was obtained
choosing the above given parameters.

### Results

![image](https://github.com/user-attachments/assets/5b5731af-b74b-4dd4-adff-d6e9eda90bce)
![image](https://github.com/user-attachments/assets/7a9f13b3-4209-431e-8cf8-ef7b44ce6c3e)
![image](https://github.com/user-attachments/assets/ce1267a0-cb0d-4090-9d58-26b4ec1359e9)

Also we got mse_loss of just 0.0019

![Accuracy](https://github.com/user-attachments/assets/8495db06-f7e4-4812-96b8-96aabaf7eeb4)


### How to Implement on your local pc

First download dataset from the following link.

https://www.kaggle.com/datasets/vasukipatel/face-recognition-dataset.

Then download the repository.

Then extract the faces folder of the dataset into the same folder as the codes.

Then first run Dataset creater to make blurred images.

Then just change in paths if needed in the main code and then run the main code and you are good to go.




