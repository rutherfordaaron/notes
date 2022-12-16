Representational State Transfer
	• REST stands for Representational State Transfer
	• It is an architectural style for providing standards between computer systems on the web, making it easier for systems to communicate with each other
		○ REST-compiant systems are also called RESTful systems
		○ These systems are characterized by how they are stateless
			§ They separate the concerns of the client and the server

Separation of Client and Server
	• With REST architecture, the client and the server can be implemented sperately
		○ Code on the client side can be changed at any time without affecting the operation of the server
		○ The coe on the server can be changed without affecting the operation of the client
	• This improves flexibility of the interface across platforms and improves scalability by simplifying the server components and allows each component to be able to evolve independently

Statelessness
	• REST sytems are stateless -- the server doesn't know anything about the state that the client is in and vice versa
		○ This way, messages sent between the client and the sever can be understood, even without seeing previous messages
		○ They rely on operation through resources, not commands
		○ They do not rely on the implementation of interfaces
	• Those constraints help RESTful apps be reliable, perfrom quickly, and be scalable
		○ Components can be managed, updated, and reused without affecting the system as a whole

Communication between Client and Server
	• The client request to retrieve or modify resources; servers send responses to those requests
Making Requests
HTTP Verbs
Headers and Accept parameters
Paths
Sending Responses
Content Types
Response Codes


Source: [What is REST? | Codecademy](https://www.codecademy.com/article/what-is-rest)