# Feature-Extraction-and-Fine-Tuning-over-VGG16

THe network evaluates two techniques for (re-)using the "experience" stored in pre-trained models. These techniques are extremely useful in the absence of the suffcient data for training a bigger model from scratch. Data such as images of 10 different classes of flowers that has been used in this work.

In the end, it has been investigated how the ConvNet actually perceives and recognizes the given data by visualizing feature maps as well performing Activation Maximization.

One thing that is typically done in computer vision tasks is to take a model trained on a very large dataset, e.g., the ImageNet ILSVRC data, and use this model for feature extraction on smaller datasets. Even though the dataset and task the model was originally trained on might be quite different to the actual dataset and task, the extracted features are typically very informative. This versatility and repurposability of ConvNets is one of the most interesting aspects of Deep Learning. The extracted features (aka representations) can then be used for downstream tasks such as classification.

The famous VGG16 model named after the Visual Geometry Group from Oxford has been employed here. The model was pre-trained on the ImageNet ILSVRC data, i.e., a large dataset of web images (1.4M images and 1000 classes). Although outperformed by more recent architectures, this simple but powerful model won the ILSVR challenge in 2014 and remains very famous for feature extraction since then. Let's see how these features help for our flower classification task!

First, an intermediate layer of VGG16 is selected that is used for feature extraction. A common practice is to use the output of the last convolution layer before the fully connected (aka dense) layers. The fully connected layers are too specialized for the original task the network was trained in. Hence using their outputs as features won't be very useful for a new task.
