## REST
- REST (short for REpresentational State Transfer) is an architectural style defined to help create and organize distributed systems.
- REST uses HTTP protocol for communication and it is widely used in web applications. REST simply provides guidelines for high-level architecture implementation on how the backend data will be available to the client via JSON/XML messaging format.
- An API uses the REST guidelines to provide web services that are ready for consumption. REST APIs provide these web services in what is called a resource. A resource represents a single state in the server and it can be accessed via a common interface, it can then be fetched or manipulated through the HTTP verbs:
	- GET
	- POST
	- DELETE
	- PUT
- A system is deemed RESTful if it meets the following constraints:
	- Client-Server
		- This constraint requires that the client and server must function independently. The server should not rely on the client to function, and the client should not depend on the server.
		- The server contains the server code and exposes the endpoints to the public via URL. The API endpoints are usually published in an API documentation, using tools like Swagger.
		- The client on the other hand knows about the API endpoints and calls them in order to get a service done and gets the response.
		- This offers a great deal of flexibility when developing both systems without them affecting each other.
		- The main principle behind this constraint is the separation of concerns. It allows for the separation of front-end code (representation and possible UI-related processing of the information) from the server-side code, which should take care of storage and server-side processing of the data.
		- The client only knows about the APIs and calls them without ever needing to know how they work. The server services are developed independently, they simply provide the interface on the payload that the client can call.
	- Stateless
	- This constraint applies that the server must save no data about the client's request. The communication must be stateless, each request must contain all information for the server.
	  The client is responsible for saving the state data in its storage.
	- This constraint makes the system highly visible and easy to inspect and debug because everything needed to know is in the request, also the system is highly scalable and reliable.
	- Cacheable
	- This constraint improves performance in both the server and the client.
	- In the server, a high-profile service that impacts the server CPU can be cached, for e.g a service that processes images, calculates huge number sequences, etc, this caching make it run only once and cache the result, then, on subsequent calls to the service, it returns the result from the cache. Other things can be cached for e.g database requests can become lengthy and the results can be cached for future requests.
	- In the client, the high profile will cause performance issues due to high load time.
	- There may be complaints of state data and the rest, that can be mitigated by using cache control, max-age, and expiry time.
	- This cacheable constraint makes the system highly performant.
	- Uniform interface
	- This constraint involves making the API interface uniform to the client. The API interface must be provided so the consumers of a service can call the service through the API interface.
	- The interface is the point publicly available so the world can communicate with your resources or services. Without the interface, the services in the server cannot be used by the consumers.
	- It is just like a library that performs a certain job, the implementation of the job i.e how the job is done is contained inside it. The library must expose functions/methods from which consumers can use to perform an action. Without the library exposing the functions/method, there is no way we can use the library.
	- Layered system
	- A server can have different layers, for e.g we can have the business logic layer, storage layer, session management layer, etc.
	- This constraint declares that the system must be layered so to allow different components to be maintained on different servers.
- The layers only communicate with the layer below to get its input and use it to communicate its output to the layer above it.
- By separating the components into layers, we make the server more flexible and very easy to maintain and scale when need be.
  Code-on-Demand
- This constraint is optional. It involves the client being able to get executable code from the server and execute it.
- This is quite unnecessary because all a client needs to do is to get information from the server and process it, but in a case where the client is a browser it becomes necessary that it should download JavaScript code, the code can enable it to process future info from the server.
- The building block of REST architecture is a resource. Everything can be a resource, it depends on the services the server will provide. These resources are accessed via a common interface using the HTTP methods.
- The HTTP verbs can be used to reference the type of action being done over a resource.
- GET Access a resource in a read-only mode.
    POST Creates a new resource.
    PUT Update a given resource.
    DELETE Removes or deletes a resource.
- If we have a product resource, we will have the below types of action to perform on the resource:
- /products GET: Get all products
    /products/:id GET: Get a given product specified by the id.
    /products:id DELETE: Remove a given product.
    /products:id PUT: Edit the given product.
    /products POST: Create a new product.
- Overview of gRPC
- gRPC is the latest framework built on top of the RPC protocol.
- gRPC is an inter-process communication that allows connection to a distributed application and calls local methods/functions in the application.
- Simply put, gRPC is an extension of RPC. In RPC, the idea is to call or invoke a remote function/method. A function can be hosted on a remote server somewhere and it can be called from another remote server or client machine not necessarily hosted on the same server.
- When developing a gRPC application, a service interface is defined. This service interface contains the methods that can be called remotely with their parameters and return types. This service interface also contains message formats that will be used when calling these methods, the argument and return types of the methods.
- So basically, a service definition interface contains the message and methods skeleton or structure.
- With this interface, the server-side service can implement this interface to provide low-level code logic. The server will provide the methods to handle the client calls.
- On the client-side, the client will use this interface too, to remotely invoke the functions. The gRPC framework abstracts away all complexities such as data serialization, network communication, authentication, access control, etc. The user knows nothing about how the communication happened.
- From what we have said above, we can deduce that a gRPC service has three components:
- The server
    The service definition interface
    The client
- gRPC server can run regardless of the environment and so is the client, it can run in any environment and they both can be written in different languages that the gRPC framework supports.
- A gRPC server can be built in Java and the client can be built in JavaScript, and they can run and talk to each other without hindrance. A gRPC server can be written in C++ while the client can be written in Go, and they can comm with each other. This is the reason gRPC is majorly preferred in many applications because they are polyglot.
  gRPC: Protocol Buffers
- The service definition interface is defined using Protocol Buffers.
- Protocol Buffers is an open-source data-serialization tool built by Google used to describe the data structure and generating a stream of bytes that represents the data.
- gRPC uses this Protocol Buffer as both IDL(Interface Definition Language) and message exchange format. This means that gRPC uses the Protocol Buffer to define the methods to be exposed by its server, e.g
- service ProductService {
    addProduct() returns () {}
    removeProduct() returns () {}
    getAllProducts() returns () {}
  }
- The above is a proto file, it defines three methods that will be exposed to and called by the client.
- As a messaging format, it defines the types just like we have in statically typed languages, we define types to show the shape of data a class, function, or a method will return, work with or receive as arg. So in Protocol Buffer, that's what messaging format does.
- message ProductRequest {
    string id = 1;
  }
- message ProductResponse {
    string name = 1;
  }
- service ProductService {
    addProduct(ProductRequest) returns (ProductResponse) {}
  }
- The object with message are the types and the messaging format to be used by both the server and the client. The addProduct method must be called with data structure as ProductRequest and it must return a data structure as ProductResponse. So both the server responding to the client class and the client calling the method must follow the ProductResponse ProductRequest formats.
- gRPC uses HTTP/2 for calls and communication. This allows users to perform the traditional request-response type of call, it can also perform one-, or two-(bidirectional) streaming.