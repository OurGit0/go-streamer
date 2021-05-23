# go-streamer

An attempt at building a distributed event streaming platform in go based on the commit log model.

Will attempt to build the following features:

- Can submit a json encoded message into a topic.
- The records in a topic are partitioned and stored in multiple nodes.
- Clients can subscribe to topics of interest and retrieve messages.

## Current usage instructions:

- run `$ go run main.go` in `go-streamer/cmd/server`
- The log protoype accepts json in the following format `{"record": {"value": "<base64 encoded value>"}}`
- you can use curl to append a message to the log with a POST request, and retrieving a message by providing an offset in a GET request

### Example 
`$ curl --request POST localhost:8080 --data '{"record": {"value": "ewogICJ1c2VybmFtZSI6InNhbnRvc2hwYXBhIiwKICAiYWdlIjogIjI5IiwKICAgInRpbWV6b25lIjogImlzdCIuCn0="}}'` for appending a message to the log. this returns json encoded offset value if there are no errors. 

`$ curl --request GET localhost:8080 --data '{"Offset":0}'` to retrieve the first entry in the log, which returns a json encoded log value with the offset.
