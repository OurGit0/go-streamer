# go-streamer

An attempt at building a distributed event streaming platform in go based on the commit log model.

Will attempt to build the following features:

- Can submit a json encoded message into a topic.
- The records in a topic are partitioned and stored in multiple nodes.
- Clients can subscribe to topics of interest and retrieve messages.
