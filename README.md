# GAN_learning
自己跑了一些比较经典的GAN模型，其中加入了部分修改

- [GAN_learning](#gan-learning)
  * [DCGAN](#dcgan)
  * [WGAN](#wgan)
    + [WGAN](#wgan-1)
    + [WGAN-gp](#wgan-gp)
    + [WGAN-div](#wgan-div)
    + [CycleGan](#cyclegan)
  * [主要参考](#主要参考)



## GAN发展概览
![一图GAN](https://user-images.githubusercontent.com/40969794/125154358-3c673580-e18c-11eb-8fda-aaea1e53ffa9.jpeg)


## DCGAN
DCGAN基本完全照搬PyTorch官方文档的代码，只在数据处理部分进行了修改。DCGAN的结构如下所示，其主要贡献是对生成器以及判别器的网络模型做了修改，使用卷积神替换掉了全连接。

![image](https://user-images.githubusercontent.com/40969794/125156504-5c045b00-e198-11eb-8bcc-7211f95aee43.png)


[[DCGAN code]](https://github.com/NanaKoori/GAN_learning/blob/master/DCGAN/dcgan_test1.py)

<br/>dcgan损失函数<br>
---
![image](https://user-images.githubusercontent.com/40969794/125088843-62df8f00-e100-11eb-9125-3fad43957ccd.png)

<br/>dcgan生成效果</br>
---
![image](https://user-images.githubusercontent.com/40969794/125088939-7d196d00-e100-11eb-9533-a1e1e9d1077d.png)



## WGAN
### WGAN
WGAN在DCGAN的基础上增加了原始的WGAN改进，包括：
- 取消掉了判别器最后一层的sigmod
- 对生成器和判别器的损失函数做了修改，不取log
- 使用一个clip对每次参数更新的结果做出了一定的截取
- 优化器改用了RMSProp

[[WGAN code]](https://github.com/NanaKoori/GAN_learning/blob/master/WGAN/wgan_test_1.py)

<br/>wgan损失函数<br>
---
![image](https://user-images.githubusercontent.com/40969794/125089063-9d492c00-e100-11eb-88c4-edd5df47a154.png)

<br/>wgan生成效果</br>
---
![image](https://user-images.githubusercontent.com/40969794/125089087-a3d7a380-e100-11eb-93c2-ab576433de21.png)
---

### WGAN-gp
WGAN-gp在WGAN的基础上又做了更改，舍弃clip转而采用gradient penalty（梯度惩罚）

[[WGAN-gp code]](https://github.com/NanaKoori/GAN_learning/blob/master/WGAN/wgan_test_2_wgan_gp.py)

<br/>wgan-gp损失函数<br>
---
![image](https://user-images.githubusercontent.com/40969794/125089272-d71a3280-e100-11eb-8ccf-bb8d261781d0.png)

<br/>wgan-gp生成效果</br>
---
![image](https://user-images.githubusercontent.com/40969794/125089458-fadd7880-e100-11eb-96a8-af6bba6572e6.png)
---

### WGAN-div
WGAN-div在WGAN-gp的基础上做出改进，对梯度惩罚的计算方式做出了改进，引入了Wasserstein Divergence（Wasserstein散度）

[[WGAN-div code]](https://github.com/NanaKoori/GAN_learning/blob/master/WGAN/wgan_test_3_wgan_div.py)

<br/>wgan-div损失函数<br>
---
![image](https://user-images.githubusercontent.com/40969794/125089698-2b251700-e101-11eb-9c68-7906d654cead.png)

<br/>wgan-div生成效果</br>
---
![image](https://user-images.githubusercontent.com/40969794/125089744-32e4bb80-e101-11eb-9725-781a2bdb0c36.png)

## PGGAN
PGGAN的核心理念是将让成器和分类器一步步放大图像的尺寸，从4×4最后放大到1024×1024。生成器和分类器也是放大一次增加一个block。而这个block的设计也是参考了resnet，因为突然放大会导致模型不稳定，用这种方法可以平滑过渡。

![image](https://user-images.githubusercontent.com/40969794/126781273-b222f097-87de-4b0f-8e98-fbe95ef91f91.png)

![image](https://user-images.githubusercontent.com/40969794/126806934-b292346c-995f-4431-b49b-416f64043e30.png)





## CycleGAN
CycleGAN通过增加一个生成网络将生成数据还原为原本数据并计算还原后的数据与原数据相似度的方法，为生成器的生成做出一定限制，实现了无监督风格迁移的模型训练。

这里推荐李宏毅老师的cycleGAN讲解：https://www.youtube.com/watch?v=wulqhgnDr7E

[[CycleGAN code]](https://github.com/NanaKoori/GAN_learning/blob/master/CycleGAN/cyclegan_test_1.py)

![image](https://user-images.githubusercontent.com/40969794/125312400-d08cf480-e366-11eb-8be9-db927c9a43a1.png)

<br/>cyclegan损失函数<br>
---
![image](https://user-images.githubusercontent.com/40969794/126637044-a7454aec-7848-48fd-8467-f3706ca8f08a.png)

<br/>cyclegan生成效果</br>
---
![10000](https://user-images.githubusercontent.com/40969794/126637446-5fd34d7a-20cf-4354-ba3b-cbb0e59695f6.png)





## 主要参考
### 代码参考：
Pytorch DCGAN的官方文档：
https://pytorch.org/tutorials/beginner/dcgan_faces_tutorial.html

eriklindernoren/PyTorch-GAN：
https://github.com/eriklindernoren/PyTorch-GAN

rosinality/progressive-gan-pytorch：
https://github.com/rosinality/progressive-gan-pytorch

### 使用数据集：
数据集使用kaggle用户提供的数据：

anime-faces：
https://www.kaggle.com/soumikrakshit/anime-faces

selfie2anime：
https://www.kaggle.com/arnaud58/selfie2anime
