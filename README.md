# Super Resolution using Generative Adversarial Network (SRGAN)

This is an implementation of the SRGAN model proposed in the paper
([Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network](
https://arxiv.org/abs/1609.04802))
with TensorFlow.

# Requirements

- Python 3
- TensorFlow 1.1
- OpenCV
- dlib

# Usage

## I. Pretrain the VGG-19 model

Download the ImageNet dataset and preprocess them with:

```
$ cd vgg19/imagenet
$ python get_urls.py
$ python create_db.py
$ python download_images.py
$ python preprocess.py
```

Train with:

```
$ cd vgg19
$ python train.py
```

Or you can download the pretrained model file:
[vgg19_model.tar.gz](
https://drive.google.com/open?id=0B-s6ok7B0V9vcXNfSzdjZ0lCc0k)


## II. Train the SRGAN (ResNet-Generator and Discriminator) model

Download the LFW dataset and preprocess them with:

```
$ cd /src/lfw
$ python lfw.py
```

Train with:

```
$ cd src
$ python train.py
```

The result will be stored in "src/result".



# Results

## LFW

![result1](results/000000001.jpg)

![result2](results/000000002.jpg)

![result3](results/000000003.jpg)

![result4](results/000000004.jpg)

![result5](results/000000005.jpg)

![result6](results/000000006.jpg)

![result7](results/000000007.jpg)

![result8](results/000000008.jpg)

![result9](results/000000009.jpg)

![result10](results/000000010.jpg)

![result11](results/000000011.jpg)

![result12](results/000000012.jpg)

![result13](results/000000013.jpg)

![result14](results/000000014.jpg)

![result15](results/000000015.jpg)

![result16](results/000000016.jpg)


# Loss function

## Adversarial loss 

This implementation adopts the least squares loss function instead 
of the sigmoid cross entropy loss function for the discriminator.
See the details: [Least Squares Generative Adversarial Networks](
https://arxiv.org/abs/1611.04076)

## Content loss

The paper says VGG54 is the perceptually most convincing results.
But this implemetation uses all the feature maps generated by every layer
(i.e. phi12, phi22, phi34, phi44, phi54) within the VGG19 network.

