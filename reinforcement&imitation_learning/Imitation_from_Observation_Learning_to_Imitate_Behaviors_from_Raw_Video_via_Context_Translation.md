Imitation from Observation: Learning to Imitate Behaviors from Raw Video via Context Translation
===
  
  The article proposes an imitation learning method based on video prediction with context translation
and deep reinforcement learning. This lifts the assumption in imitation learning that the demonstration should consist
of observations in the same environment configuration, and enables a variety of interesting applications  
  The experimental results show the effectiveness of the approach in learning a wide range of real-world robotic
tasks modeled after common household chores from videos.But,** human's hand or body can't appearce in video **.  

本文使用一个语义转换的视频预测神经网络来学习大量的演示经验，并拿其推理某一视角下初始时刻之后的图像状态，再拿预测到的视频的每一帧图像的
欧几里得距离来做Reward函数，再利用深度强化学习来实现任务  
缺点：场景不可改变，从实验结果中发现人类的手或者身体不能出现在视频中  
疑问：是否只能预测初始图像而不能预测任务中途的图像
