
You can run cifar10_train.py. You can do this by command line: `python cifar10_train.py --version='test'`. You may also change the version number inside the hyper_parameters.py file

The training and validation error will be output on the screen. They can also be viewed using tensorboard. Use `tensorboard --logdir='logs_$version'` command to pull them out. (For e.g. If the version is ‘test’, the logdir should be ‘logs_test’.) 
The relevant statistics of each layer can be found on tensorboard.  

### Pre-requisites
pandas, numpy , opencv, tensorflow(1.0.0)

### Overall structure
There are four python files in the repository. cifar10_input.py, resnet.py, cifar10_train.py, hyper_parameters.py.

cifar10_input.py includes helper functions to download, extract and pre-process the cifar10 images. 
resnet.py defines the resnet structure.
cifar10_train.py is responsible for the training and validation.
hyper_parameters.py defines hyper-parameters related to train, resnet structure, data augmentation, etc. 


### Test
The test() function in the class Train() help you predict. It returns the softmax probability with shape [num_test_images, num_labels]. You need to prepare and pre-process your test data and pass it to the function. You may either use your own checkpoints or the pre-trained ResNet-110 checkpoint I uploaded. You may wrote the following lines at the end of cifar10_train.py file
```
train = Train()
test_image_array = ... # Better to be whitened in advance. Shape = [-1, img_height, img_width, img_depth]
predictions = train.test(test_image_array)
# predictions is the predicted softmax array.
```
Run the following commands in the command line:
```
# If you want to use my checkpoint. 
python cifar10_train.py --test_ckpt_path='model_110.ckpt-79999'
```
   
