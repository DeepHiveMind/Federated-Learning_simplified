# Federated-Learning

## Agenda

- What is Federated Learning?
- Federated Learning in a Nutshell
- Benefits
- Federated Learning Framework
- Recent Advances in Federate Learning
- Challenges
- Conclusion

## What is Federated Learning?

The field of machine learning is constantly evolving, sometimes slowly, and at other times we experience the tech equivalent of the Cambrian Explosion with rapid advance that makes a good many data scientists experience a serious case of imposter syndrome. Take the case of a new iteration of machine learning called “federated learning” that was first introduced by Google AI in 2017 in a blog post “[Federated Learning: Collaborative Machine Learning without Centralized Training Data](https://ai.googleblog.com/2017/04/federated-learning-collaborative.html)” along with a now seminal research paper that set the stage for federated learning with a deep discussion of a new approach called federated optimization “[Federated Optimization: Distributed Machine Learning for On-Device Intelligence](https://arxiv.org/pdf/1610.02527.pdf)” (Oct. 2016). In just a few years, this new methodology has taken significant strides forward.

In this page we’ll explore federated learning in terms of its beginnings, benefits, challenges, as well as some recent advances.

## Federated Learning in a Nutshell

Traditional machine learning involves a data pipeline that uses a central server (on-prem or cloud) that hosts the trained model in order to make predictions. The downside of this architecture is that all the data collected by local devices and sensors are sent back to the central server for processing, and subsequently returned back to the devices. This round-trip limits a model’s ability to learn in real-time.

```Federated learning (FL) in contrast, is an approach that downloads the current model and computes an updated model at the device itself (ala edge computing) using local data. These locally trained models are then sent from the devices back to the central server where they are aggregated, i.e. averaging weights, and then a single consolidated and improved global model is sent back to the devices.```

![alt text](https://github.com//DeepHiveMind/Federated-Learning/blob/main/example.png?raw=true)

*Your phone personalizes the model locally, based on your usage (A). Many users’ updates are aggregated (B) to form a consensus change © to the shared model, after which the procedure is repeated.
Source: [https://ai.googleblog.com/2017/04/federated-learning-collaborative.html](https://ai.googleblog.com/2017/04/federated-learning-collaborative.html)*

In a more general sense, FL allows for machine learning algorithms to gain experience from a broad range of data sets located at different locations. The approach enables multiple organizations to collaborate on the development of models, but without needing to directly share secure data with each other. Over the course of several training iterations, the shared models get exposed to a significantly wider range of data than what any single organization possesses in-house. In other words, FL decentralizes machine learning by removing the need to pool data into a single location. Instead, the model is trained in multiple iterations at different locations.

Google describes how FL works in this way with respect to mobile phones:

```It works like this: your device downloads the current model, improves it by learning from data on your phone, and then summarizes the changes as a small focused update. Only this update to the model is sent to the cloud, using encrypted communication, where it is immediately averaged with other user updates to improve the shared model. All the training data remains on your device, and no individual updates are stored in the cloud.```

## Benefits

Here are some primary benefits of federated machine learning:

- FL enables devices like mobile phones to collaboratively learn a shared prediction model while keeping the training data on the device instead of requiring the data to be uploaded and stored on a central server.
- Moves model training to the edge, namely devices such as smartphones, tablets, IoT, or even “organizations” like hospitals that are required to operate under strict privacy constraints. Having personal data remain local is a strong security benefit.
- Makes real-time prediction possible, since prediction happens on the device itself. FL reduces the time lag that occurs due to transmitting raw data back to a central server and then shipping the results back to the device.
- Since the models reside on the device, the prediction process works even when there is no internet connectivity.
- FL reduces the amount of hardware infrastructure required. FL uses minimal hardware and what is available in mobile devices is more than enough to run the FL models.


## Federated Learning Framework
Here are several new available FL framework/libraries:
- [TensorFlow Federated (TFF)](https://www.tensorflow.org/federated) and also on [GitHub](https://github.com/tensorflow/federated)
      - [Tensorflow Federated Tutorials](https://federated.withgoogle.com/)
- [FLOWER](https://flower.dev/) and also on [GitHub](https://github.com/adap/flower)
      - Framework-agnostic: Different machine learning frameworks have different strengths. Flower can be used with any machine learning framework, for example, PyTorch, TensorFlow, MXNet, or even raw NumPy for users who enjoy computing gradients by hand.
      - Flower (flwr) is a framework for building federated learning systems.Please see [Flower_Framework.md](Flower_Framework.md) to get started!
- [NVFlare by NVIDIA](https://docs.nvidia.com/clara/clara-train-sdk/federated-learning/federated_learning.html) as an integral offering within "NVIDIA CLARA". It uses pyTorch.
      - [NVIDIA CLARA Notebooks iPython samples](https://github.com/DeepHiveMind/Federated-Learning/blob/main/README_NVIDIA_CLARA.md)
- [PySyft by openmined](https://www.openmined.org/) and also on [GitHub](https://github.com/OpenMined/PySyft)


## Recent Advances in Federate Learning

Due to the importance of what FL brings to the table for machine learning in a hyper-connected world, this technology has become a fertile area of research. For example, a simplistic implementation of the FL framework requires that each device sends a full model (or full model update) back to the central server for each round. For larger models, this step can create a bottleneck due to factors like asymmetric internet connection speeds (e.g. slower upload speeds versus download). New research such as “[Federated Learning: Strategies for Improving Communication Efficiency](https://arxiv.org/pdf/1908.07873.pdf)” (Oct. 2017), investigates methods which can reduce the uplink communication costs.

Additionally, a number of groups are working to review the unique characteristics and challenges of FL and provide a detailed perspective for current approaches, and assess directions for future work that are relevant to a range of application areas. A recent paper, “[Federated Learning: Challenges, Methods, and Future Directions](https://arxiv.org/pdf/1902.01046.pdf)” (Aug. 2019) by a group of Carnegie Mellon University researchers established the fact that FL is an active and ongoing area of research and provided an extensive summary of recent work.

There is also a paper that describes a scalable production system for FL for mobile devices, “Towards Federated Learning at Scale: System Design” (Mar. 2019) which includes the resulting high-level design, overview of new challenges with solutions, and also some open problems with future directions.

## Challenges

There are a number of core challenges associated with FL. First, communication is a critical bottleneck in FL networks where data generated on each device remain local. In order to train a model using data generated by the devices in the network, it is necessary to develop communication-efficient methods that reduce the total number of communication rounds, and also iteratively send small model updates as part of the training process, as opposed to sending the entire data set.

Additionally, FL methods must: anticipate low levels of device participation, i.e. only a small fraction of the devices being active at once; tolerate variability in hardware that affects storage, computational, and communication capabilities of each device in a federated network; and be able to handle dropped devices in the network.

Finally, FL helps to protect data generated on a device by sharing model updates such as gradient data instead of raw data. But communicating model updates throughout the training process can still reveal sensitive information, either to a third party, or to the central server.


## Conclusion

In this page, we’ve introduced a new setting for distributed machine learning (optimization problems), which is called federated learning. This setting is motivated by the methodology where users do not send the data they generate locally to central servers at all, but rather provide part of their computational power to be used to perform local machine learning training. This comes with a unique set of challenges however FL researchers are actively engaged with bringing this new technology forward. Still not convinced that FL holds much promise? Check out the [Google Manga description](https://federated.withgoogle.com/), it may get you off the fence!



