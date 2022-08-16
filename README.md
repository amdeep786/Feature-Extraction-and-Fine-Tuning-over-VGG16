# Feature-Extraction-and-Fine-Tuning-over-VGG16

In the last lab, you built a simple ConvNet, trained it from scratch, added augmentation and regularization techniques, and achieved about 90% accuracy.

In this homework, you will use two techniques for (re-)using the "experience" stored in pre-trained models. These techniques are extremely useful if you don't have suffcient data for training a bigger model from scratch. Data such as our images of 10 different classes of flowers. ;-)

In detail, you will use transfer learning and fine-tuning of a model that was already trained on a very large dataset, namely the ImageNet ILSVRC data.

In the end, you will investigate how our ConvNet actually perceives and recognizes the given data by visualizing feature maps as well performing Activation Maximization.

After completing this homework you will be able to

Use pretrained models for transfer-learning and fine-tuning
alter the train scope of specific layers of your models
interprete what your model has learned.


One thing that is typically done in computer vision tasks is to take a model trained on a very large dataset, e.g., the ImageNet ILSVRC data, and use this model for feature extraction on smaller datasets. Even though the dataset and task the model was originally trained on might be quite different to the actual dataset and task, the extracted features are typically very informative. This versatility and repurposability of ConvNets is one of the most interesting aspects of Deep Learning. The extracted features (aka representations) can then be used for downstream tasks such as classification.

In this homework, you will use the famous VGG16 model named after the Visual Geometry Group from Oxford. The model was pre-trained on the ImageNet ILSVRC data, i.e., a large dataset of web images (1.4M images and 1000 classes). Although outperformed by more recent architectures, this simple but powerful model won the ILSVR challenge in 2014 and remains very famous for feature extraction since then. Let's see how these features help for our flower classification task!

First, we need to pick which intermediate layer of VGG16 we will use for feature extraction. A common practice is to use the output of the last convolution layer before the fully connected (aka dense) layers. The fully connected layers are too specialized for the original task the network was trained in. Hence using their outputs as features won't be very useful for a new task.

The zoo of pre-trained models is provided in the keras.applications module in TF. You can directly load the architecture from there. If you set weights='imagenet', the imagenet weights will be loaded automatically.

If include_top=False is specified, the network is loaded without the original classification layers at the top. Instead the network's last layer is a MaxPooling2D layer pooling across the output of the last convolution layer.
