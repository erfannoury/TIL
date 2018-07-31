Never forget to set `model.eval()` before doing evaluations. This is very very important for checking correctness and also comparing the model outputs (especially if you are doing model comparison between PyTorch and TensorFlow).

----

Dense weigths in PyTorch are saved as `[Out, In]`. However, when using these weights in TensorFlow it will not suffice to just transpose them. The first fully-connected layer after the last convolutional layer is problematic. PyTorch uses `NCHW` data format. If you use `NHWC` data format in TensorFlow, you need to do additional work to correctly convert the weights to TensorFlow format. Remember that `In = C x H x W`. So the weight matrix first needs to be reshaped to `[Out, C, H, W]`. After that it should be transposed to `[Out, H, W, C]`. Then you can reshape it back to its original shape and do a matrix transpose if needed.

----
