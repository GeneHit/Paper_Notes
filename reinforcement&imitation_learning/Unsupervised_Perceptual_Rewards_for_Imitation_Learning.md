Unsupervised Perceptual Rewards for Imitation Learning
===
Understanding level(1-5): *2*  
**Abstract**:   
>leveraging the abstraction power of intermediate visual representations learned by deep models that pre-trained to quickly infer perceptual reward functions from small numbers of demonstrations. It present a method that is able to identify key intermediate steps of a task from
only a handful of demonstration sequences, and automatically identify the most discriminative features for identifying these steps.  
  
   **issues**:  
>many interesting tasks consist of multiple implicit intermediate steps that must be executed in sequence. Even when the final outcome can be measured, it does not necessarily provide feedback on these intermediate steps or sub-goals.  
  
   **initial idea**:
>1. imitation makes use of extensive prior knowledge to quickly glean the “gist” of anew task from even a small number of demonstrations;  
>2. imitation involves both observation and trial-and-error learning(RL).  
>To:a reward learning method for understanding the intent of a user demonstration through the use of pre-trained visual features, which provide the “prior knowledge” for efficient imitation.
  
  **Aims**  
>to discover not only the high-level goal of a task, but also the implicit sub-goals and steps that comprise more complex behaviors.
  
   **main idea**:  
>Algorithm
  
   **shortcoming**:  
>it proposes to address differences in context by using pretrained visual features, but does not provide for
any mechanism for context translation
