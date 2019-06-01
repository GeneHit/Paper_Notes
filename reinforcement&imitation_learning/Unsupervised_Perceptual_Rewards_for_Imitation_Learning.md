Unsupervised Perceptual Rewards for Imitation Learning
===
Understanding level(1-5): *3*  
**Abstract**:   
>leveraging the abstraction power of intermediate visual representations learned by deep models that pre-trained to quickly infer perceptual reward functions from small numbers of demonstrations. It present a method that is able to identify key intermediate steps of a task from
only a handful of demonstration sequences, and automatically identify the most discriminative features for identifying these steps.  
  
   **issues**:  
>many interesting tasks consist of multiple implicit intermediate steps that must be executed in sequence. Even when the final outcome can be measured, it does not necessarily provide feedback on these intermediate steps or sub-goals.  
  
   **main idea**:
>1. imitation makes use of extensive prior knowledge to quickly glean the “gist” of anew task from even a small number of demonstrations;  
>2. imitation involves both observation and trial-and-error learning(RL).  
  
>==>:  
a reward learning method for understanding the intent of a user demonstration through the use of pre-trained visual features, which provide the “prior knowledge” for efficient imitation.
  
  **aims**  
>to discover not only the high-level goal of a task, but also the implicit sub-goals and steps that comprise more complex behaviors.
  
  **method**:  
>**method overview**  
>1. Giving a few demonstration videos of the same action.  
>2. Discovering intermediate steps.  
>3. Training a classifier for each step on top of the mid and high-level representations of a pre-trained deep model.  
>4. The step classifiers are then combined to produce a single reward function per step prior to learning. These intermediate rewards are combined into a single reward function.  
>5. The reward function is used by a real robot to learn the perform the demonstrated task.  
  
  **amazing experient**
>1.liquid pouring  
2.**learn a complex real-world door opening skill**
  
  **shortcoming**:  
>it proposes to address differences in context by using pretrained visual features, but does not provide for
any mechanism for context translation
