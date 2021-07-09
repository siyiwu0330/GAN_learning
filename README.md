# GAN_learning
自己跑了一些比较经典的GAN模型，其中加入了部分修改，并使用统一的anime faces数据集

- [GAN_learning](#gan-learning)
  * [DCGAN](#dcgan)
  * [WGAN](#wgan)
    + [WGAN](#wgan-1)
    + [WGAN-gp](#wgan-gp)
    + [WGAN-div](#wgan-div)
  * [主要参考](#----)


## DCGAN
DCGAN基本完全照搬PyTorch官方文档的代码，只在数据处理部分进行了修改

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


## 主要参考
### 代码参考：
Pytorch DCGAN的官方文档：
https://pytorch.org/tutorials/beginner/dcgan_faces_tutorial.html

eriklindernoren/PyTorch-GAN：
https://github.com/eriklindernoren/PyTorch-GAN

### 使用数据集：
数据集使用kaggle用户提供的数据：
https://www.kaggle.com/soumikrakshit/anime-faces
