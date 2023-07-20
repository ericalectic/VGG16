#Introduction
This repository presents the research findings and enhancements made to the VGG-16 model, a popular deep learning architecture known for its effectiveness in image classification tasks. The goal of this undergraduate thesis is to propose modifications to the VGG-16 model that aim to improve its performance, accuracy, and computational efficiency.

#Methodology
The modifications applied to the VGG-16 model are as follows:

Concatenation of Intermediate Layer Outputs:
    After extracting features from the VGG-16 base model, we perform depth concatenation on the downsampled feature maps of different layers (block1_conv2, block2_conv2, block3_conv3, block4_conv3, and block5_conv3).  This enables the model to capture multi-scale information from different levels of abstraction, enhancing its ability to recognize intricate patterns in the data.
    
Downsampled and Upsampled Connections:
    Downsampled and upsampled connections are introduced between different blocks of the VGG-16 model.  Outputs of block1_conv2, block2_conv2, block3_conv3, block4_conv3, and block5_conv3 are downsampled and then upsampled before concatenating them together.This multi-scale feature fusion strategy facilitates the integration of information from various spatial resolutions, enhancing the model's capacity to understand both fine-grained and high-level features.
    
Batch Normalization Layers:
  Batch normalization layers (bn1, bn2, bn3, bn4, and bn5) are added after some of the convolutional layers. Batch normalization helps in normalizing the activations, which stabilizes and accelerates the training process, leading to faster convergence and improved overall performance.

Global Average Pooling:
  We introduce a GlobalAveragePooling2D layer (gap6) after the block6_conv1 layer. Global average pooling reduces the spatial dimensions of the feature maps to a vector by taking the average of each feature map. This technique reduces the number of parameters and provides a fixed-length representation, making the model more memory-efficient and less prone to overfitting.

Dense Classification Layer:
  A Dense layer (fc12) with 4 units and softmax activation is added as the final classification layer. This layer maps the learned features to the corresponding class probabilities, allowing the model to make accurate predictions.

Implementation Details
  To ensure the enhancements to the VGG-16 model are effective, we made the following changes:

Freezing of Original VGG-16 Layers:
  We freeze the original VGG-16 model's layers to retain the pre-trained weights, as these weights capture valuable general knowledge from a large dataset. By setting layer.trainable = False for each layer in the base model, we ensure that only the newly added layers are trained while keeping the pre-trained features intact.

Activation Function Modification:
  The last activation function of the model is modified from softmax to sigmoid for binary classification tasks.  This adaptation allows the model to handle binary classification efficiently, making it more versatile in different scenarios. Checkpointing and Plotting:

