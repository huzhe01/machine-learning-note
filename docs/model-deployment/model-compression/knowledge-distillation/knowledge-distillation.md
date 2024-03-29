# 知识蒸馏

- [返回上层目录](../model-compression.md)



===

[机器学习：残差学习、RNN、GAN、迁移学习、知识蒸馏](https://blog.csdn.net/holly_Z_P_F/article/details/122337962)

知识蒸馏指的是将复杂模型（teacher）中学到的知识迁移到简单模型（student）中去。
一般来说，我们认为teacher模型具有强大的能力和表现，而student模型则体量很小。通过知识蒸馏，希望student模型能尽可能逼近亦或是超过teacher模型，从而用更少的复杂度来获得类似的预测效果，实现模型的压缩和量化。

上面说的迁移学习，一般认为模型的参数保留了模型学到的知识，常见的迁移学习的方式就是在一个大的数据集上先做预训练，然后使用预训练得到的参数在一个小的数据集上做fine-tuning(两个数据集往往领域不同或者任务不同)，例如先在Imagenet上做预训练，然后在COCO数据集上做检测。

蒸馏神经网络想做的事情，本质上很接近迁移学习。（知识蒸馏开山之作：Hinton的Distilling the Knowledge in a Neural Network。）论文中，作者认为可以将模型看成是黑盒子，知识可以看成是输入到输出的映射关系。因此，我们可以先训练好一个teacher网络，然后将teacher的网络的输出结果 q作为student网络的目标，训练student网络，使得student网络的结果pred接近q。
所以，整个做法就是先训练一个teacher网络，然后使用这个teacher网络的输出和数据的真实标签去训练student网络。从而将一个网络的知识转移到另一个网络，也可以将多个网络学到的知识转移到一个网络中去。
————————————————
版权声明：本文为CSDN博主「1900_」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：