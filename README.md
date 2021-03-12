# Federated-Learning

## Agenda

- What is Federated Learning?
- Federated Learning in a Nutshell
- Benefits
- Challenges
- Recent Advances in Federate Learning
- Federated Learning Framework
- Conclusion

## What is Federated Learning?

The field of machine learning is constantly evolving, sometimes slowly, and at other times we experience the tech equivalent of the Cambrian Explosion with rapid advance that makes a good many data scientists experience a serious case of imposter syndrome. Take the case of a new iteration of machine learning called “federated learning” that was first introduced by Google AI in 2017 in a blog post “Federated Learning: Collaborative Machine Learning without Centralized Training Data” along with a now seminal research paper that set the stage for federated learning with a deep discussion of a new approach called federated optimization “Federated Optimization: Distributed Machine Learning for On-Device Intelligence” (Oct. 2016). In just a few years, this new methodology has taken significant strides forward.

In this page we’ll explore federated learning in terms of its beginnings, benefits, challenges, as well as some recent advances.

## Federated Learning in a Nutshell

Traditional machine learning involves a data pipeline that uses a central server (on-prem or cloud) that hosts the trained model in order to make predictions. The downside of this architecture is that all the data collected by local devices and sensors are sent back to the central server for processing, and subsequently returned back to the devices. This round-trip limits a model’s ability to learn in real-time.

Federated learning (FL) in contrast, is an approach that downloads the current model and computes an updated model at the device itself (ala edge computing) using local data. These locally trained models are then sent from the devices back to the central server where they are aggregated, i.e. averaging weights, and then a single consolidated and improved global model is sent back to the devices.



