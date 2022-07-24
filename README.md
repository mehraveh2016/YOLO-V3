# YOLO-V3
Input 
Yolo inputs contains two parts : the images and their labels. Before feeding the input to the network we should create the label that can be produced in different formats. In this project, the labels are txt files which we used “labeling” for creation. Each txt file includes bounding box coordinates (x, y, width and height) and the class number (we assign a number to each class).

When the feature map ready the network passes it to Activation Function which in the case of yolo v3 is ReLu(is a nonlinear function).In this version we have in some convolutions we have batch normalization which is the factor that normalize the output of the layer, it helps the layer to learn independently

Architecture
The YOLO version 3 architecture, like other versions is based on convolutional neural network. This specific object detection algorithm’s backbone is darknet-53 which contains 75 convolutional layers.

In this version, we have 4 kind of different convolutional layers:
	Convolutional layer type1 which have batch normalization specification and its activation function is ReLu, 
	Convolutional layer type2 , in that layer there no batch normalization, the activation function is linear , also he system calculate the filter size with use of ((number of classes+5)+3)
	Down sample: this layer is used for prevention of loss of the low levels feature in the network 
	Up sample: is the inverse of down sampling layer.

The  original YOLO outputted a single 7x7 grid which was great for the large pictures. YOLO v3 makes the prediction across 3 scales which the detection layer use to make different feature maps, the sizes are 8,16 and 32. Striding is using for downsampling.
If our dataset contains the images with the size of 416x416, and the network uses the stride with 8, 16, 32, the feature maps as output will be 13x13, 26x26 and 52x52 respectively. The 13x13 detects large objects, 26x26 is for medium objects and 52x52 is used for the small size objects. ⌊((n-f)/s┤ ├ )+1⌋ is the formula for calculating the output while using stride.
(n= is image height/width, f kernel size and s are the stride )

YOLO V3 ‘s kernel size is: 1x1 and 3x3.

Recovering the output form previous layer and forward it to the next layer is the role of route layer in the network.

The yolo layer is the layer which the network detects the objects inside the images. In yolo version 3, the network detects the objects in 3 scales, for this reason we have 3 yolo layers, first layer is 84th, in this layer, the network separates the small objects , the output is 13x13, second yolo layer in 96th, is the medium size object detection , output is 26x26  and finally the last layer of the network which also id the 3rd yolo layer, layer number 106 which determines the large objects and give an output with the size of 52x52. 
