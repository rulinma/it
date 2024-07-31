# 生成对抗网络

GAN(Generative Adversarial Networks)

GAN 由两个主要组件组成：生成假样本的生成器和区分真实样本和生成器生成样本的判别器。生成器和鉴别器可以说是互相竞争的关系。他们都是独立训练的，在训练过程中，他们玩的是零和游戏。生成器不断生成欺骗判别器的假样本，而判别器则努力发现那些假样本（参考真实样本）。在每次训练迭代中，生成器在生成接近真实的假样本方面做得更好，判别器必须提高标准来区分不真实的样本和真实样本。

* 生成模型（Generative Model）
* 判别模型（Discriminative Model

https://github.com/nashory/gans-awesome-applications
