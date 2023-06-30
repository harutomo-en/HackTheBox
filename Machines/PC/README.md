# HackTheBox - PC
### Rating - Easy

gRPC running on port 50051, using grpcurl we can list the services that are running on the port

request: ```grpcurl -plaintext 10.10.11.214:50051 list```

response: ```SimpleApp
grpc.reflection.v1alpha.ServerReflection```

Now that we know the services that are running on gRPC, we can use the grpcurl to list the commands available on each of the services.

request: ```grpcurl -plaintext 10.10.11.214:50051 list SimpleAPP```
request: ```grpcurl -plaintext 10.10.11.214:50051 list grpc.reflection.v1alpha.ServerReflection```

There are three commands available on the SimpleApp:

```SimpleApp.LoginUser```

```SimpleApp.RegisterUser```

```SimpleApp.getInfo```

The SimpleApp service appears to be a basic user account handling application.

There is only one command available for the grpc.reflection.v1alpha.ServerReflection service:

```grpc.reflection.v1alpha.ServerReflection.ServerReflectionInfo```


Attempting to register a user using SimpleApp.RegisterUser works
you can also login

however using gRPCurl is showing missing header token even when trying to define the token header

uses a JWT for authentication

found admin user on the gRPC with password also being admin
was able to log in using the SimpleApp.LoginUser

