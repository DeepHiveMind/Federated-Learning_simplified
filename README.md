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


In a more general sense, FL allows for machine learning algorithms to gain experience from a broad range of data sets located at different locations. The approach enables multiple organizations to collaborate on the development of models, but without needing to directly share secure data with each other. Over the course of several training iterations, the shared models get exposed to a significantly wider range of data than what any single organization possesses in-house. In other words, FL decentralizes machine learning by removing the need to pool data into a single location. Instead, the model is trained in multiple iterations at different locations.

Google describes how FL works in this way with respect to mobile phones:

```It works like this: your device downloads the current model, improves it by learning from data on your phone, and then summarizes the changes as a small focused update. Only this update to the model is sent to the cloud, using encrypted communication, where it is immediately averaged with other user updates to improve the shared model. All the training data remains on your device, and no individual updates are stored in the cloud.```

## Benefits

Here are some primary benefits of federated machine learning:

FL enables devices like mobile phones to collaboratively learn a shared prediction model while keeping the training data on the device instead of requiring the data to be uploaded and stored on a central server.
Moves model training to the edge, namely devices such as smartphones, tablets, IoT, or even “organizations” like hospitals that are required to operate under strict privacy constraints. Having personal data remain local is a strong security benefit.
Makes real-time prediction possible, since prediction happens on the device itself. FL reduces the time lag that occurs due to transmitting raw data back to a central server and then shipping the results back to the device.

Since the models reside on the device, the prediction process works even when there is no internet connectivity.


