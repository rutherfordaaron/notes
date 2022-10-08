What is HTTP?
	• HTTP: Hypertext Transfer Protocol
		○ It is used to structure requests and responses over the internet
	• Tranfering resources happens with TCP: Transmission Control Protocol
		○ TCP manages the channels between the browser and the server and is used to manage many types of internet connection
	• HTTP is the command language that the devices on oth sides of the connection must follow in order to communicate

HTTP & TCP: How it Works
	• When you type an addressinto your browser, you're commanding it to open a TCP channel to the server that responds to that URL
		○ URL: Unifrom Resource Locator
	• Once the TCP connection is established, the client sends an HTTP GET request to the server to retrieve the webpage to be displayed
		○ Once the response is sent, the TCP connection is closed
		○ If you open the website again or if the browser automatically requests something from the server, a new connection is opened and the process happens again

What is HTTPS?
	• HTTPS is the same as HTTP but is (S) secure
		○ It allows you to encrypt data that you send and receive
	• It's important to use HTTPS when passig sensitive or personal information to and from websites
		○ It's up to the business mainaining the servers to set it up
		○ In order to support HTTPS, the business must apply for a certifacte from a Certificate Authority

Source: [HTTP Requests | Codecademy](https://www.codecademy.com/article/http-requests)