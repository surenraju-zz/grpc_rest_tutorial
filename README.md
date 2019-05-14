# grpc_rest_tutorial

This project aims to teach a ```gRPC``` service with ```HTTP+JSON``` interface. A small amount of configuration in your service to attach HTTP semantics is all that's needed to generate a reverse-proxy with this library.

Installation
The grpc-gateway requires a local installation of the Google protocol buffers compiler protoc v3.0.0 or above. Please install this via your local package manager or by downloading one of the releases from the official repository:

```https://github.com/protocolbuffers/protobuf/releases```

Then, ```go get -u``` as usual the following packages:
```
go get -u github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway
go get -u github.com/grpc-ecosystem/grpc-gateway/protoc-gen-swagger
go get -u github.com/golang/protobuf/protoc-gen-go
```
This will place three binaries in your ```$GOBIN```;

- ```protoc-gen-grpc-gateway```
- ```protoc-gen-grpc-swagger```
- ```protoc-gen-go```

Start terminal to build and run gRPC server with HTTP/REST gateway (replace parameters according to your SQL database server):
```
cd cmd/server
go build .
server.exe -grpc-port=9090 -http-port=8080 -db-host=<HOST>:3306 -db-user=<USER> -db-password=<PASSWORD> -db-schema=<SCHEMA>
```
If you see
```
2019/05/14 17:28:25 starting HTTP/REST gateway...
2019/05/14 17:28:25 starting gRPC server...
```
It means server is started. Open another terminal to build and run HTTP/REST client:
```
cd cmd/client-rest
go build .
client-rest.exe -server=http://localhost:8080
```
If we see something like this
```
2019/05/14 17:24:04 Create response: Code=200, Body={"api":"v1","id":"2"}
2019/05/14 17:24:04 Read response: Code=200, Body={"api":"v1","toDo":{"id":"2","title":"title (2019-05-14T11:54:04.3968122Z)","description":"description (2019-05-14T11:54:04.3968122Z)","reminder":"2019-05-14T11:54:04Z"}}
2019/05/14 17:24:04 Update response: Code=200, Body={"api":"v1","updated":"1"}
2019/05/14 17:24:04 ReadAll response: Code=200, Body={"api":"v1","toDos":[{"id":"2","title":"title (2019-05-14T11:54:04.3968122Z) + updated","description":"description (2019-05-14T11:54:04.3968122Z) + updated","reminder":"2019-05-14T11:54:04Z"}]}
2019/05/14 17:24:04 Delete response: Code=200, Body={"api":"v1","deleted":"1"}
```
Everything works fine



Reference
https://medium.com/@amsokol.com/tutorial-how-to-develop-go-grpc-microservice-with-http-rest-endpoint-middleware-kubernetes-af1fff81aeb2
