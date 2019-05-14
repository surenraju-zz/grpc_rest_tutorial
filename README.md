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


