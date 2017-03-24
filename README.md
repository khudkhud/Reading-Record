# Reading-Record
#### 1. Active Object Localization with Deep Reinforcement Learning
>#### Abstract
>We present an active detection model for localizing objects in scenes. The model is class-specific and allows an agent to focus attention on candidate regions for identifying the correct location of a target object. This agent learns to deform a bounding box using simple transformation actions, with the goal of determining the most specific location of target objects following top-down reasoning. The proposed localization agent is trained using deep reinforcement learning, and evaluated on the Pascal VOC2007 dataset.
> ##### 1. Introduction
>In this work, we propose a class-specific active detection model that learns to localize target objects known by the system. The proposed model follows a top-down search strategy, which starts by analyzing the whole scene and then proceeds to narrow down the correct location of objects. This is achieved by applying a sequence of transformations to a box that initially covers a large region of the image and is finally reduced to tight bounding box. The sequence of transformations is decided by an agent that analyzes the content of the currently visible region to select the next best action. Each transformation should keep the object inside the visible region while cutting off as much background as possible.
>We propose a dynamic attention-action strategy that requires to pay attention to the contents of the current region, and to transform the box in such a way that the target object is progressively more focused.
> ##### 2.Previous Works
> ##### 3.Object Localization as Dynamic Decision Process

#### 2.Simple Online and realtime tracking
>#### Abstract
>This paper explores a pragmatic approach to multiple object tracking where the main focus is to associate objects efficiently for online and realtime applications.Despite only using a rudimentary combination of familiar techniques such as the **Kalman Filter** and **Hungarian algorithm** for the tracking components, this approach achieves an accuracy comparable to state-of-the-art online trackers. Furthermore, due to the simplicity of our tracking method, the tracker updates at a rate of **260 Hz** which is over 20x faster than other state-of-the-art trackers.