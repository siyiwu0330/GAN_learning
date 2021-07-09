# GAN_learning
项目旨在跑通一些比较经典的GAN模型，其中加入了部分修改



## 已实现的模型
### DCGAN
损失函数
![image](https://user-images.githubusercontent.com/40969794/125088843-62df8f00-e100-11eb-9125-3fad43957ccd.png)
生成效果
![image](https://user-images.githubusercontent.com/40969794/125088939-7d196d00-e100-11eb-9533-a1e1e9d1077d.png)


### WGAN
#### WGAN
损失函数
![image](https://user-images.githubusercontent.com/40969794/125089063-9d492c00-e100-11eb-88c4-edd5df47a154.png)
生成效果
![image](https://user-images.githubusercontent.com/40969794/125089087-a3d7a380-e100-11eb-93c2-ab576433de21.png)

#### WGAN-gp
损失函数
![image](https://user-images.githubusercontent.com/40969794/125089272-d71a3280-e100-11eb-8ccf-bb8d261781d0.png)
生成效果
![image](https://user-images.githubusercontent.com/40969794/125089458-fadd7880-e100-11eb-96a8-af6bba6572e6.png)

#### WGAN-div
损失函数
![image](https://user-images.githubusercontent.com/40969794/125089698-2b251700-e101-11eb-9c68-7906d654cead.png)
生成效果
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
