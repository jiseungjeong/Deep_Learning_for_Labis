# FCN(fully convolution network)์ ๊ดํ์ฌ


<aside>
๐ก ์ถ์ฒ: [https://wikidocs.net/147359](https://wikidocs.net/147359)

</aside>

> ์ด๋ฏธ์ง ๋ถ๋ฅ์์ ์ฐ์ํ ์ฑ๋ฅ์ ๋ณด์ธ **CNN๊ธฐ๋ฐ์ ๋ชจ๋ธ(AlexNet, VGG16, GoogLeNet)์ semantic seg. task(์ฌ๋ฌ ํด๋์ค๋ก ํฝ์ ๋ถ๋ฅํ๋ task)๋ฅผ ์ํํ  ์ ์๋๋ก ๋ณํํ ๋ชจ๋ธ**
> 

โ ์ ์ด ํ์ต์ผ๋ก ๊ตฌํํจ

โ ์ดํ ๋์จ segmentation seg. task๋ค์ ์ฃผ๋ก fcn์ ๊ธฐ๋ฐ์ผ๋ก ๋ง๋ค์ด์ง.

# **์ด๋ฏธ์ง ๋ถ๋ฅ(image classfication)**


์ด๋ฏธ์ง ๋ด์ ๋ชจ๋  ํฝ์์์ ํผ์ณ ์ถ์ถํ๊ณ ,

์ถ์ถํ ํผ์ณ๋ค์ classifier์ ๋ฃ์ด ์ ์ฒด(total) ์๋ ฅ ์ด๋ฏธ์ง์ ํด๋์ค๋ฅผ ์์ธก

# **์ด๋ฏธ์ง ๋ถํ (Image seg.)**


**์ด๋ฏธ์ง๋ฅผ ์ด๋ฃจ๋ ๋ชจ๋  ํฝ์๋ค์ class๋ฅผ ์์ธกํ๋ task**์.

์ด๋ฏธ์ง ๋ถ๋ฅ์์ ์ฐ์ธ pretain ๋คํธ์ํฌ์์ feature extraction ๋ ์ด์ด๋ ์ฌํ์ฉํ์ฌ feature๋ฅผ ์ถ์ถํ๊ณ  fully connected layer(dense layer)๋ฅผ ๋ฒ๋ฆฌ๊ณ  1*1 conv์ up-scaling(transpose convolution)์ผ๋ก ๋ณ๊ฒฝํ์ฌ (fine tuning) ํฝ์ ํด๋์ค ๋ถ๋ฅ์ ์ด๋ฏธ์ง๋ ๊ฐ์ ํฌ๊ธฐ๋ฅผ ์์ํ์ผ๋ก ํ๋๋ก ํจ.

![Untitled](/Deep%20Learning%20from%20Scratch/FCN/Untitled.png)

โ upscaling

# **Fully connected layer(FC layer) ์ด๋?(= dense layer)**


CNN์์ 	๋ ์ด์ด๋ ํฌ๊ฒ 2๊ฐ์ง ์ ํ์ผ๋ก ๋๋๋ค.

- Convolution/pooling layer: ์ด๋ฏธ์ง๋ฅผ (filter ํตํด) ๋ถํ ํ๊ณ  ๋ถ์
- FC layer: ์ด๋ฏธ์ง๋ฅผ ๋ถ๋ฅํ๊ณ  ์ค๋ชํ๋ ๋ฐ ๊ฐ์ฅ ์ ํฉํ๊ฒ ์์ธก์ ํ๋ ์ธต

์ด์ค FC layer๋ ๋ค์๊ณผ ๊ฐ์ ์ญํ ์ ํ๋ค.

- flattening: ํํํ, ์ด์  ๋ ์ด์ด์ ์ถ๋ ฅ์ ํํํํ์ฌ ๋ค์ ๋ ์ด์ด์ ์๋ ฅ์ด ๋  ์ ์๋ ๋จ์ผ ๋ฒกํฐ๋ก ๋ณํํจ
- ๋จผ์  ์๋ ฅ์ ์ทจํ์ฌ ๋ผ๋ฒจ์ ์์ธกํ๊ธฐ ์ํด ๊ฐ์ค์น๋ฅผ ์ ์ฉํ๊ณ , ๊ฐ ๋ผ๋ฒจ์ ๋ํ ์ต์ข ํ๋ฅ ์ ์ ๊ณตํจ.
- ์ฆ convolution/pooling ํ๋ก์ธ์ค์ ๊ฒฐ๊ณผ๋ฅผ ์ทจํ์ฌ ์ด๋ฏธ์ง๋ฅผ ๋ผ๋ฒจ๋ก ๋ถ๋ฅํ๋๋ฐ ์ฌ์ฉํจ.(์ต์ข ๋ถ๋ฅ ๋ ์ด์ด)

# **๋คํธ์ํฌ ๊ตฌ์กฐ**


![Untitled](/Deep%20Learning%20from%20Scratch/FCN/Untitled%201.png)

1. Convolution layer๋ก feature ์ถ์ถ
2. 1*1 convolution layer๋ฅผ ์ด์ฉํ์ฌ feature map์ ์ฑ๋์๋ฅผ ๋ฐ์ดํฐ์์ ๊ฐ์ฒด์(# of instance)์ ๋์ผํ๊ฒ ๋ณ๊ฒฝ (class presence heat map ์ถ์ถ)
3. Up-sampling: ๋ฎ์ ํด์๋์ heat map์ upsampling(=transposed convolution) ํ๊ณ , ์๋ ฅ ์ด๋ฏธ์ง์ ๊ฐ์ ํฌ๊ธฐ์ map ์์ฑ
4. ์ต์ข ํผ์ฒ ๋งต๊ณผ ๋ผ๋ฒจ ํผ์ฒ๋งต์ ์ฐจ์ด๋ฅผ ์ด์ฉํ์ฌ ๋คํธ์ํฌ ํ์ต

![Untitled](/Deep%20Learning%20from%20Scratch/FCN/Untitled%202.png)

๋ง์ง๋ง 7*7 ํผ์ฒ ๋งต์ ํ ํฝ์์ ๊ธฐ์กด ์ธํ ์ด๋ฏธ์ง์ 32*32 pixel์ ๋ํํ๊ฒ ๋๋๋ฐ, ์ด๋ฅผ ์์ํ๋งํ๋ ๊ณผ์ ์์ ๊ธฐ์กด ์ด๋ฏธ์ง์ ์ ๋ณด๊ฐ ์์ค๋  ์ ์๋ค.(๋ญ๊ทธ๋ฌ์ง ๋ฌธ์ ) ๋ฐ๋ผ์ ์์ํ๋ง์ ํ  ๋ ํผ์ฒ ์ถ์ถ ๋จ๊ณ์ ํผ์ฒ๋งต๋ ์์ํ๋ง์ ํฌํจ(sum)ํ์ฌ ์ ๋ณด ์์ค์ ๋ง๋ ๋ฐฉ๋ฒ์ ์ฌ์ฉํจ.(**skip architecture, ์ด๋ ํ๋ผ๋ฏธํฐ์ ํฐ ์ฆ๊ฐ ์์ด ์ฑ๋ฅ์ ๋น์ฝ์ ์ผ๋ก ํฅ์์ํด**)

์ด๋ ๋จ๊ณ์ ํผ์ฒ์ถ์ถ๋จ๊ณ๊น์ง๋ฅผ ๋ฐ์ํ๋๋์ ๋ฐ๋ผ ์ ํ๋๊ฐ ๋ฌ๋ผ์ง๋ค.(์ด๊ธฐ์ ํผ์ฒ์ถ์ถ๋จ๊ณ๋ถํฐ ๊ณ ๋ คํ ์๋ก img. Seg. ์ ํ๋๊ฐ ๋์์ง๋ค.)

![Untitled](/Deep%20Learning%20from%20Scratch/FCN/Untitled%203.png)

์ด๋ฏธ์ง ๋ถํ ์ ํ๋ fcn์ ์ด๋ฏธ์ง ๋ถ๋ฅ ๋ชจ๋ธ์ ์ฌ์ฉํ๊ธฐ์, ์ด๋ฏธ์ง ๋ถ๋ฅ ๋ชจ๋ธ์ด ๋ฐ๋ฌํ ์๋ก, ์ด๋ฏธ์ง ๋ถํ  ๋ชจ๋ธ์ ์ฑ๋ฅ์ด ํฅ์๋จ.(์ด๋ฏธ์ง ๋ถ๋ฅ ๋คํธ์ํฌ์์ ์ถ์ถํ๋ ํผ์ณ๋ฅผ ์ด๋ฏธ์ง ๋ถํ ์์๋ ์์ ์์ด ์ฌ์ฉ๊ฐ๋ฅํ๊ธฐ ๋๋ฌธ)

# **FC layer๋ฅผ ์ญ์ ํจ์ผ๋ก์จ ์ด๋ฏธ์ง ๋ถํ ์ ๊ตฌํํจ**


FC layer๋ฅผ ์ด์ฉํ์ฌ ์ด๋ฏธ์ง ๋ถํ ์ ํ๋ ๊ฒ์ ์ ํฉํ์ง ์์.

1. FC layer๋ฅผ ํต๊ณผํ๊ณ  ๋๋ฉด ์ด๋ฏธ์ง์ ์์น ์ ๋ณด๊ฐ ์ฌ๋ผ์ง๊ธฐ ๋๋ฌธ
(์ปจ๋ณผ๋ฃจ์ ๋ ์ด์ด๋ ์์น์ ๋ณด๊ฐ ์ ์ฅ๋๋ ๋ฐ๋ฉด FC layer๋ ์์น ์ ๋ณด๊ฐ ์ฌ๋ผ์ง)
2. FC layer๋ ๊ณ ์ ๋ ํฌ๊ธฐ์ input image๋ง ๋ฐ์ ์ ์๊ธฐ ๋๋ฌธ
(Dense layer์ **๊ฐ์ค์น ๊ฐ์๊ฐ ๊ณ ์ **๋์ด ์๊ธฐ ๋๋ฌธ์ ๋ฐ๋ก ์ ๋ ์ด์ด์ Feature Map์ ํฌ๊ธฐ๋ ๊ณ ์ ๋จ
3. FC layer๋ ํ๋ผ๋ฏธํฐ ๊ฐ์๋ฅผ ๋๋ฌด ๋ง์ด ํ์๋ก ํจ
(fully connected ์ด๊ธฐ ๋๋ฌธ)

์ด๋ฐ ์ด์ ๋ก FC layer๋ฅผ ์ญ์ ํ๊ณ  1*1 convolution์ผ๋ก ๋์ฒดํจ.

# **FCN์์๋ deconvolution์ ์ฌ์ฉํ๋๊ฐ ์๋ transposed convolution์ ์ฌ์ฉํ๋๊ฐ?**


๊ฐ์ ๊ฐ๋์ผ๋ก ์ฌ์ฉํ๋ ๊ฒฝํฅ์ด ์๋๋ฏ, convolution์ ์ญ์ฐ์ฐ์ deconvolution์ด๋ผ๊ณ  ํ๋๋ฐ, ๊ทธ ์ญ์ฐ์ฐ ์์ transposed convolution์ด ํฌํจ๋๋ ๋ฏ

[https://gaussian37.github.io/vision-segmentation-fcn/](https://gaussian37.github.io/vision-segmentation-fcn/) fcn pytorch๋ก ๊ตฌํ(ํ๊ธ)

https://github.com/divamgupta/image-segmentation-keras โ fcn ๊ธฐ๋ฐ ๋ชจ๋ธ๋ค์ ๊ตฌํํด๋์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ

[https://github.com/divamgupta/image-segmentation-keras/blob/master/keras_segmentation/models/fcn.py](https://github.com/divamgupta/image-segmentation-keras/blob/master/keras_segmentation/models/fcn.py) โ ์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ์์ ๊ตฌํํ fcn ๋ชจ๋ธ ์ ์ฒด ์ฝ๋

# ํ์ดํผ ํ๋ผ๋ฏธํฐ๋?

๋ชจ๋ธ์ ์ธ ๋ ์ฌ์ฉ์๊ฐ ์ง์  ์ค์ ํ๋ ๊ฐ(์ต์ ์ ๊ฐ์ด ์์ผ๋ฉฐ ๊ฒฝํ ๋ฒ์น์ผ๋ก ๊ฒฐ์ ๋๋ ๊ฒฝ์ฐ๊ฐ ๋ง๋ค.)์ด๋ค. ๋ฐ๋ฉด ํ๋ผ๋ฏธํฐ๋ ๋ชจ๋ธ ํน์ ๋ฐ์ดํฐ์ ์ํด ๊ฒฐ์ ๋๋ค.

# **์ฌ์ฉํ  ํ์ดํผํ๋ผ๋ฏธํฐ/ ์ ๋๋ณผ๊ณณ**

[https://github.com/pytorch/vision/blob/bf843c664b8ba0ff49d2921237500c77d82f2d04/torchvision/models/segmentation/fcn.py#L9](https://github.com/pytorch/vision/blob/bf843c664b8ba0ff49d2921237500c77d82f2d04/torchvision/models/segmentation/fcn.py#L9) โ Fully Convolutional Networks for Semantic Seg.(CVPR 2015) ๋ผ๋ฌธ FCN ๋ชจ๋ธ ํ์ด์ฌ ์ฝ๋

```python
from torch import nn

from ._utils import _SimpleSegmentationModel

__all__ = ["FCN"]

class FCN(_SimpleSegmentationModel):
    """
    Implements a Fully-Convolutional Network for semantic segmentation.

    Arguments:
        backbone (nn.Module): the network used to compute the features for the model.
            The backbone should return an OrderedDict[Tensor], with the key being
            "out" for the last feature map used, and "aux" if an auxiliary classifier
            is used.
        classifier (nn.Module): module that takes the "out" element returned from
            the backbone and returns a dense prediction.
        aux_classifier (nn.Module, optional): auxiliary classifier used during training
    """
    pass

class FCNHead(nn.Sequential):
    def __init__(self, in_channels, channels):
        inter_channels = in_channels // 4
        layers = [
            nn.Conv2d(in_channels, inter_channels, 3, padding=1, bias=False),
            nn.BatchNorm2d(inter_channels),
            nn.ReLU(),
            nn.Dropout(0.1),
            nn.Conv2d(inter_channels, channels, 1)
        ]
# in_channels -(with filter size 3)-> in_channels//4 -(with_filter size 1)->1
# ->up-sampling
        super(FCNHead, self).__init__(*layers) #๋ถ๋ชจ ํด๋์ค(nn.Sequential) ํธ์ถ ๋ฐ ์ด๊ธฐํ
```

- ์ธ์ฝ๋์ ๋์ฝ๋ ๊ตฌ์กฐ(์ผ๋ง๋ ๋ณต์กํ๊ฒ ๋ง๋ค๊ฒ์ธ์ง, ๋ฌด์จ ๋ฐฉ์ ์ฌ์ฉํ  ๊ฒ์ธ์ง)
    - up-sampling ๋ฐฉ์(์ผ๋ฐ์ ์ผ๋ก๋ transpose convolution์ ์ฐ๋ ๋ฏ)
    - CNN ๊ธฐ๋ฐ ๋ชจ๋ธ ๋ญ ์ฑํํ ์ง (+CNN์ ํ๋ผ๋ฏธํฐ๋ค)
    - Skip architecture
- Data augmentation(๋ฐ์ดํฐ์ ๋ฐ๋ฅธ augmentation ๋ฐฉ์)
- ๋ถ๋ฅํ  ํด๋์ค ์
- ์๋ ฅ ์ด๋ฏธ์ง ํฝ์ ํฌ๊ธฐ
- batch normalization ๋น์จ
- ์ด๋ฏธ์ง ํฌ๋กญ ์ฌ๋ถ

<aside>
๐ก ์๋ง ์ด๋ฒ ์ฐฝ์ํ์์ ์ฐพ์ผ๋ผ๋ FCN ๋ชจ๋ธ์ ์ด๊ธฐ FCN๋ชจ๋ธ์ ๊ธฐ๋ฐ์ผ๋ก ๋ณํ๋ ๊ฒ๊น์ง ํฌํจํ๋ ๊ฐ๋์ผ๋ก ๋ณด์. ์ง์  ํ์ฉ์ ํ๊ธฐ ์ํ ๋ชจ๋ธ์ ์ฐพ๋ ๊ฒ์ด ์ค์ํ๋ฐ, ๋ง์ฝ ์ฐ๋ฆฌ๊ฐ ์ด๊ธฐ FCN ๋ชจ๋ธ๋ง ์ฐพ๋๋ค๋ฉด ํ์ฉ ํ์ต๋ณด๋ค๋ ์ด๋ก  ํ์ต์ ๋ ๊ฐ๊น๊ธฐ ๋๋ฌธ.

</aside>

# ๋ด๊ฐ ์๊ฐํ๋ FCN์ ํน์ง ์ด๋?

๊ธฐ์กด CNN ๋ชจ๋ธ์ ๋ง์ง๋ง dense ์ธต์ ๋นผ๊ณ  1*1 ์ปจ๋ณผ๋ฃจ์ ๋ ์ด์ด์ up-sampling ๊ตฌ์กฐ๋ฅผ ๋ฃ์ ๊ฒ์ผ๋ก ๊ธฐ์กด ์ธํ๊ณผ ๊ฐ์ ํฌ๊ธฐ์ ์์ํ์ ๋ด๋๋๋ค. ์ฃผ๋ก ์ด๋ฏธ์ง ๋ถํ ์ ์ฌ์ฉ๋๋ค. 

<aside>
๐ก ํ๊ณ  ์ถ์ ์ง๋ฌธ
1. ์ง๊ธ ํ๊ณ ์ ํ๋ task๊ฐ image segmentation์ธ๊ฐ, ํน์ instance segmentation์ธ๊ฐ(๋ฏธ๋ ๋ฐฉํฅ์ฑ์ ์ค๋ฆฝํ๋๋ฐ ์ค์ํ ์ง๋ฌธ์.)

</aside>

# ์๋ณธ ์ด๋ฏธ์ง์ Label๋ ์ด๋ฏธ์ง ๋ฐ์ดํฐ

[https://www.kaggle.com/code/vanvalkenberg/image-segmentation-u-net-for-self-driving-cars/data](https://www.kaggle.com/code/vanvalkenberg/image-segmentation-u-net-for-self-driving-cars/data) โ Cambridge labeled data

[https://www.kaggle.com/code/sgorl1234/image-segmentation-for-self-driving-cars/data](https://www.kaggle.com/code/sgorl1234/image-segmentation-for-self-driving-cars/data) โ์๋ณธ๊ณผ label์ด ํฉ์ณ์ ธ ์์(cityscapes_data)