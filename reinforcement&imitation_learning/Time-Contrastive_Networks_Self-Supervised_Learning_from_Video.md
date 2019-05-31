Time-Contrastive Networks: Self-Supervised Learning from Video
===
understanding level(1-5):*3*

文章提出一个结合Time-Contrastive Networks和deep network的网络结构，以第一人称视角的t、t+k时刻的图像及第三人称的时刻的图像作为输入
（也可全利用single-view的video）来学习一个特征输出，再利用这一特征与robot视角的输入图像的欧几里得空间距离（特别设计公式）来作为Reward，
再利用强化学习来找到当前最优策略。  
其中，文中说用到已经训练好的网络，这部分是利用ImageNet-pretrained Inception model来构建TCN network.
疑问：Time-Contrastive Networks在训练时的loss函数是单独设计的，其特征输出与loss函数没有直接关系，貌似特征是从TCN的网络结构中间得到，需要对
TCN network有一个理解。
