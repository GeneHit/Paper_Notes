Unsupervised Perceptual Rewards for Imitation Learning
===
Understanding level(1-5): *2*  
**Abstract**:   
    issues:many interesting tasks consist of multiple implicit intermediate steps that must be executed in sequence. Even when the final 
outcome can be measured, it does not necessarily provide feedback on these intermediate steps or sub-goals.
    main idea:leveraging the abstraction power of intermediate visual representations learned by deep models that pre-trained to quickly 
infer perceptual reward functions from small numbers of demonstrations. We present a method that is able to identify key intermediate steps of a task from
only a handful of demonstration sequences, and automatically identify the most discriminative features for identifying these steps.
    shortcoming:it proposes to address differences in context by using pretrained visual features, but does not provide for
any mechanism for context translation
