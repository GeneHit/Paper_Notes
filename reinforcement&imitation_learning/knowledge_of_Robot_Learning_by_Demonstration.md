Robot learning by demonstration
===
**Robot Learning from Demonstration (LfD)** or **Robot Programming by Demonstration (PbD)** (also known as **Imitation Learning** and 
**Apprenticeship Learning**) is a paradigm for enabling robots to autonomously perform new tasks. Rather than requiring users to 
analytically decompose and manually program a desired behavior, work in LfD - PbD takes the view that an appropriate robot controller can 
be derived from observations of a human's own performance thereof. The aim is for robot capabilities to be more easily extended and 
adapted to novel situations, even by users without programming ability.  
      
    Contents:  
    1 Overview  
      1.1 Principle  
      1.2 Historical Context  
    2 Key Issues in Programming by Demonstration / Learning from Demonstration  
      2.1 What to imitate and Evaluation Metric  
      2.2 How to Imitate and the Notion of Correspondence  
      2.3 Interfaces for Demonstration  
    3 Ways to Solve LfD - PbD  
      3.1 Low level learning of individual motions  
      3.2 Learning high-level action composition  
    4 Imitation Learning combined with Other Learning Techniques  
      4.1 Imitation Learning and Reinforcement Learning(#imitation-learning-and-reinforcement-learning)  
      4.2 LfD - PbD and Human-Robot Interaction  
      4.3 Limitations and Open Questions  
    5 Further Reading  
  
Overview
---
* **Principle**  
The main principle of robot LfD-PbD is that end-users can teach robots new tasks without programming.  
In a traditional programming scenario, a human programmer would have to reason in advance and code a robot controller that is capable of 
responding to any situation the robot may face, no matter how unlikely. This process may involve breaking down the task into 100s of 
different steps, and thoroughly testing each step. If errors or new circumstances arise after the robot is deployed, the entire costly 
process may need to be repeated, and the robot recalled or taken out of service while it is fixed.  
In contrast, LfD - PbD allows the end-user to 'program' the robot simply by showing it how to perform the task - no coding required. Then,
when failures occur, the end-user needs only to provide more demonstrations, rather than calling for professional help. LfD - PbD hence 
seeks to endow robots with the ability to learn what it means to perform a task by generalizing from observing several demonstrations.  
* **Historical Context**  
Robot Learning from Demonstration started in the 1980s. Then, and still to a large extent now, robots had to be tediously hand programmed 
for every task they performed. LfD - PbD seeks to minimize, or even eliminate, this difficult step by letting users train their robot to 
fit their needs. The expectation is that the methods of LfD-PbD, being user-friendly, will allow robots to be utilized to a greater extent 
in day-to-day interactions with non-specialist humans. Furthermore, by utilizing expert knowledge from the user, in the form of 
demonstrations, the actual learning should be fast compared to current trial-and-error learning, particularly in high dimensional spaces 
(henceforth addressing part of the well-known curse of dimensionality).

Key Issues in Programming by Demonstration / Learning from Demonstration
---
[Nehaniv & Dautenhahn (2001)][Nehaniv] phrased the problems faced by LfD - PbD in a set of key questions: '’'What to imitate? How to 
imitate? When to imitate? Whom to imitate?'’' To date, only the first two questions have really been addressed in LfD - PbD.  
* **What to imitate and Evaluation Metric**
What to imitate relates to the problem of determining which aspects of the demonstration should be imitated. For a given task, certain 
observable or affectable properties of the environment may be irrelevant and safely ignored. Key to determining what is and is not 
important is understanding the metric by which the robot's behavior is being evaluated.  

* **How to Imitate and the Notion of Correspondence**  
1. Perceptual equivalence:Due to differences between human and robot sensory capabilities, the same scene may appear very different to 
each. For instance, while a human may identify humans and gestures from light, a robot may use depth measurements to observe the same 
scene.Another point of comparison is tactile sensing. Most tactile sensors allow robots to perceive contact, but do not offer 
information about temperature, in contrast to the human skin. Moreover, the low resolution of the robots' tactile sensors does not 
allow robots to discriminate across the variety of existing textures, while human skin does. As the same data may therefore not be 
available to both humans and robots, successfully teaching a robot may require a good understanding of the robot's sensors and their 
limitations. LfD - PbD explores the limits of these perceptual equivalences, by building interfaces that either automatically correct 
for or make explicit these differences.  
2. Physical equivalence: Due to differences between human and robot embodiments, humans and robots may perform different actions to 
accomplish the same physical effect.  
Solving this discrepancy in motor capabilities is akin to solving the How to imitate problem and is the focus of much work in LfD - PbD.
For example, a robot may compute a path (in Cartesian space) for its end-effector that is close to the path followed by the human, while
relying on inverse kinematics to find the appropriate joint displacements to deal with the fact that the two bodies are different. In the
football example above, this would require the robot to determine a path for its center of mass which corresponds to the path followed 
by the human's right foot when projected on the ground. Clearly, this equivalence is very task-dependent.  
Taken together, these two equivalences deal with discrepancies in how robots and humans are embodied. We can think of the perceptual 
equivalence as dealing with the manner in which the agents perceive the world, and makes sure that the information necessary to perform 
the task is available to both. Physical equivalence deals with the manner in which agents affect and interact with the world, and makes 
sure that the task is actually performable by both.  

* **Interfaces for Demonstration**  
The interface used to provide demonstrations plays a key role in the way the information is gathered and transmitted. We distinguish 
three major trends:  
A) Directly recording human motions.   
B) Kinesthetic teaching, where the robot is physically guided through the task by the humans.  
C) Immersive teleoperation scenarios, where a human operator is limited to using the robot's own sensors and effectors to perform the task.  

Ways to Solve LfD - PbD
---
Current approaches to encoding skills through LfD - PbD can be broadly divided between two trends:  
1)**a low-level representation of the skill, taking the form of a non-linear mapping between sensory and motor information**  
2)**a high-level representation of the skill that decomposes the skill in a sequence of action-perception units**  

Imitation Learning combined with Other Learning Techniques
---
The majority of work in LfD - PbD focuses solely on learning from demonstration data. There is however a growing body of works that 
look at ways in which LfD - PbD can be combined with other learning techniques. One group of work investigates how to combine imitation 
learning with reinforcement learning, a method by which the robot learns through trial and error, so as to maximize a reward. Other 
works take inspiration in the way humans teach each other and introduce interactive and bidirectional teaching scenarios whereby the 
robot becomes an active partner during the teaching. We briefly review the main principles underlying each of these areas below:  
* **Imitation Learning and Reinforcement Learning**  
A major limitation of imitation learning is that the robot can only become as good as the human's demonstrations. There is no additional
information for improving the learnt behavior. Reinforcement learning, in contrast, allows the robot to discover new control policies 
through free exploration of the state-action space, but often takes a long time to converge. Approaches that combine the two aim at 
exploiting the strength of both to overcome their respective drawbacks. Particularly, demonstrations are used to initiate and guide the 
exploration done during reinforcement learning, reducing the time to find an improved control policy, which may depart from the 
demonstrated behavior.  
    * Inverse Reinforcement Learning/Learning the Reward Function
    Typically, works that combine imitation learning with reinforcement learning assume a known reward to guide the exploration. In 
    contrast, Inverse Reinforcement Learning (IRL) offers a framework to automatically determine the reward and discover the optimal 
    control policy (Abbeel and Ng 2004). When using human demonstrations to guide learning, IRL is solving jointly the What to imitate 
    and How to imitate problems, see [examples of Inverse Reinforcement Learning](http://www.scholarpedia.org/article/Robot_learning_by_demonstration/Current_Work#Inverse_Reinforcement_Learning).
    While the original approach assumes a Markov world (i.e. discrete state action space), alternative approaches derive a cost function in a continuous space (Ratliff et al 2006, 2009), 
    and include extensions of IRL for continuous state-action space (Howard et al. 2013). Note that these works are closely related to 
    inverse optimal control, a large area of research in control theory.  
    Underlying all IRL works is the assumption of a consistent reward function. When demonstrations are provided by multiple experts, 
    this assumes that all experts optimize the same objectives. This is constraining and does not exploit the variability of ways in 
    which humans may solve the same task.  
    In all previous examples, there is a reliance on successful demonstrations of the desired task by the human. LfD-PbD techniques 
    assume that all the demonstrations are good demonstrations and researchers generally discard data that are poor proxy of what would 
    be deemed as a good behavior. Recent work has begun to investigate the possibility that demonstrations corresponding to failed 
    attempts at performing the task may be useful for learning (Grollman and Billard, 2011; Ray et al. 2013). In this case, LfD - PbD 
    expands to learn both what to and what not to imitate. This work offers an interesting alternative to approaches that combine 
    imitation learning and reinforcement learning, in that no reward needs to be explicitly determined, see also [Learning from Failure](http://www.scholarpedia.org/article/Robot_learning_by_demonstration/Current_Work#Learning_from_Failure).
* **LfD - PbD and Human-Robot Interaction**  
As LfD - PbD necessarily deals both with humans and robots, it overlaps heavily with the field of Human Robot Interaction (HRI). In 
addition to the learning algorithms themselves, many human-centric issues are researched as part of LfD - PbD. Generally, the focus is 
on how to better elicit and utilize the demonstrations.  
New lines of research seek to make the teaching/learning process more interactive.  
* **Limitations and Open Questions**  
Research in LfD-PbD is progressing rapidly, pushing back limits and posing new questions all the time. As such, any list of limitations and open questions is bound to be incomplete and out of date. However, there are a few long-standing limitations and open questions that bear further attention.
Generally, work in LfD-PbD assumes a fixed, given form for the robot's control policy, and learns appropriate parameters. To date, there are several different forms of policies in common usage, and there is no clear correct (or dominant) technique. Furthermore, it is possible that a system could be provided with multiple possible representations of controllers and select which is most appropriate.
The combination of reinforcement learning and imitation learning has been shown effective in addressing the acquisition of skills that require fine tuning of the robot's dynamics. Likewise, more interactive learning techniques have proven successful in allowing for collaborative improvement of the learnt policy by switching between human-guided and robot-initiated learning. But, there do not yet exist protocols to determine when it is best to switch between the various learning modes available. The answer may in fact be task-dependent.
In work to date, teaching is usually done by a single teacher, or teachers with an explicit concept of the task to teach. More work need to be done to address issues related to conflicting demonstrations across teachers with different styles. Similarly, teachers are usually human beings, but could instead be an arbitrary expert agent. This agent could be a more knowledgeable robot or a computer simulation.
Experiments in LfD-PbD have mostly focused on a single task (or set of closely related tasks) and each experiment starts with a tabula rasa. As learning of complex tasks progresses, means to store and reuse prior knowledge at a large scale will have to be devised. Learning stages, akin perhaps to those found in child development, may be required. There will need to be a formalism to allow the robot to select information, to reduce redundant information, select features, and store efficiently new data.

Further Reading
---


[Nehaniv]:http://www.scholarpedia.org/article/Robot_learning_by_demonstration#LikeMe
