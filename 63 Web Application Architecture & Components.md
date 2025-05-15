# 63 Web Application Architecture & Components

## Web Application Architecture

- Web application architecture refers to the structure and organization of components and technologies used to build a web application.
- It defines how different parts of the application interact with each other to deliver its functionality, handle user requests, and manage data.
- A well-designed web application architecture is crucial for ensuring scalability, maintainability, and security.
- Before performing a security assessment on a web application, it is vitally important to know how web applications work with regards to the underlying architecture. This knowledge will provide you with a much better understanding of where and how to identify and exploit potential vulnerabilities or misconfigurations in web applications.


## Client-Server Model

- Web applications are typically built on the client-server model. In this architecture, the web application is divided into two main components:
	- **Client**
		- The client represents the user interface and user interaction with the web application. It is the front-end of the application that users access through their web browsers. The client is responsible for displaying the web pages, handling user input, and sending request to the server for data or actions.
	- **Server**
		- The server represents the back-end of the web application. It processes client requests, executes the application's business logic, communicates with databases and other services, and generates responses to be sent back to the client. 


 ```mermaid
graph TD
    subgraph Web Application
        WS[Web Server]
        DB[Database]
        WS <--> DB
    end

    U1[User 1]
    U2[User 2]
    U3[User 3]

    U1 --> WS
    U2 --> WS
    U3 --> WS
```


## Web Application Components

| **Component**                | **Function**                                                                                                                                                                                                                                                                 |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **User Interface (UI)**      | The user interface is the visual presentation of the web application seen and interacted with by users. It includes elements such as web pages, forms, menus, buttons, and other interactive components.                                                                     |
| **Client-Side Technologies** | Client-side technologies, such as HTML (Hypertext Markup Language), CSS (Cascading Style Sheets), and JavaScript, are used to create the user interface and handle interactions directly within the user's web browser.                                                      |
| **Server-Side Technologies** | Server-side technologies, such as programming languages (e.g., PHP, Python, Java, Ruby) and frameworks, are used to implement the application's business logic, process requests from clients, access databases, and generate dynamic content to be sent back to the client. |
| **Databases**                | Databases are used to store and manage the web application's data. They store user information, content, configurations, and other relevant data required for the application's operation.                                                                                   |
| **Application Logic**        | The application logic represents the rules and procedures that govern how the web application functions. It includes user authentication, data validation, security checks, and other business rules.                                                                        |
| **Web Servers**              | Web servers handle the initial request from clients and serve the client-side components, such as static files (HTML, CSS, JavaScript), to the users.                                                                                                                        |
| **Application Servers**      | Application servers execute the server-side code and handle the dynamic processing of client requests. They communicate with databases, perform business logic, and generate dynamic content.                                                                                |

## Client-side Processing

-  Client-side processing involves executing tasks and computations on the user's device, typically within their web browser.
- The client-side refers to the user's end of the web application, where the web browser and user interface reside.
- Client-side processing has some limitations. It is not suitable for handling sensitive or critical operations, as it can be easily manipulated by users or malicious actors.
- Key characteristics of client-side processing:
	- User Interaction: Client-side processing is well-suited for tasks that require immediate user interaction and feedback, as there is no need to send data back and forth to the server.
	- Responsive User Experience: Since processing happens locally, client-side operations can provide a smoother and more responsive user experience.
	- JavaScript: JavaScript is the primary programming language used for client-side processing. It allows developers to manipulate the web page's content, handle user interactions, and perform validations without involving the server.
	- Data Validation: Client-side validation ensures that user input meets specific criteria before it is sent to the server, reducing the need to make unnecessary server requests.


## Server-side Processing

- Server-side processing involves executing tasks and computations on the web server, which is the remote computer where the web application is hosted.
- The server-side refers to the backend of the web application, where the business logic and data processing take place.
- Key characteristics of server-side processing:
	- Data Processing: Server-side processing is ideal for tasks that involve sensitive data handling, complex computations, and interactions with databases or external services.
	- Security: Since server-side code is executed on a trusted server, it is more secure than client-side code, which can be manipulated by users or intercepted by attackers.
	- Server-side languages: Programming languages like PHP, Python, Java, Ruby, and others are commonly used for server-side processing.
	- Data Storage: Server-side processing enables secure storage and management of sensitive data in databases or other storage systems. 


## Communication & Data Flow

- Web applications communicate over the internet using HTTP (Hypertext Transfer Protocol).
- When a user interacts with the web application by clicking on links or submitting forms, the client sends HTTP requests to the server.
- The server processes these requests, interacts with the database if necessary, performs the required actions, and generates an HTTP response.
- The response is then sent back to the client, which renders the content and presents it to the user.


# Web Application Technologies

- Understanding web technologies is essential for anyone involved in web development, web application security or web application security testing/web application penetration testing.
- As a web application penetration tester, you will be frequently interacting, assessing and exploiting the underlying technologies that make up a web application as a whole.
- As a result, you need to have a fundamental understanding of what server-side and client-side technologies make up a web application and what their functionalities are and when and why they are deployed.


## Client-Side Technologies

- HTML (Hypertext Markup Language)
	- HTML is the markup language used to structure and define the content of web pages. It provides the foundation for creating the layout and structure of the UI.
- CSS (Cascading Style Sheets)
	- CSS is used to define the presentation and styling of web pages. It allows developers to control the colors, fonts, layout, and other visual aspects of the UI.
- JavaScript
	- JavaScript is a scripting language that enables interactivity in web application. It is used to create dynamic and responsive IU elements, handle user interaction, and perform client-side validations.
- Cookies and Local Storage
	- Cookies and local storage are client-side mechanism to store small amounts of data on the user's browser. They are often used for session management and remembering user preferences. 


## Server-Side Technologies

- Web Server
	- The web server is responsible for receiving and responding to HTTP requests from clients (web browsers). It hosts the web application's files, processes requests, and sends responses back to clients. (Apache2, Nginx, Microsoft IIS etc) 
- Application Server
	- The application server runs the business logic of the web application. It processes user requests, accesses databases, and performs computations to generate dynamic content that the web server can serve to clients.
- Database Server
	- The database server stores and manages the web application's data. It stores user information, content, configurations, and other relevant data required for the application's operation. (MySQL, PostgreSQL, MSSQL, Oracle etc)
- Server-side Scripting Languages
	- Server-side scripting languages (e.g., PHP, Python, Java, Ruby) are used to handle server-side processing. They interact with databases, perform validations, and generate dynamic content before sending it to the client.


## Communication & Data Flow

- Web applications communicate over the internet using HTTP (Hypertext Transfer Protocol).
- When a user interacts with the web application by clicking on links or submitting forms, the client sends HTTP requests to the server.
- The server processes these requests, interacts with the database if necessary, performs the required actions, and generates an HTTP response.
- The response is then sent back to the client, which renders the content and presents it to the user.


## Data Interchange

- Data interchange refers to the process of exchanging data between different computer systems or applications, allowing them to communicate and share information.
- It is a fundamental aspect of modern computing, enabling interoperability and data sharing between diverse systems, platforms, and technologies.
- Data interchange involves the conversion of data from one format to another, making it compatible with the receiving system.
- This ensures that data can be interpreted and utilized correctly by the recipient, regardless of the differences in their data structures, programming languages, or operating systems.


## Data Interchange Technologies

- APIs (Application Programming Interfaces)
	- APIs allow different software systems to interact and exchange data. Web applications use APIs to integrate with external services, share data, and provide functionalities to other applications.


## Data Interchange Protocols

- JSON (JavaScript Object Notation)
	- JSON is a lightweight and widely used data interchange format that is easy for both humans and machines to read and write. It is based on JavaScript syntax and primarily used for transmitting data between a server and a web application as an alternative to XML.
- XML (eXtensible Markup Language)
	- XML is a versatile data interchange format that uses tags to define the structure of the data. It allows users to create their custom tags and define complex hierarchical data structures. XML is commonly used for configuration files, web services, and data exchange between different systems.
- REST (Representational State Transfer)
	- REST is a software architectural style that uses standard HTTP methods (GET, POST, PUT, DELETE) for data interchange. It is widely used for creating web APIs that allow applications to interact and exchange data over the internet.
- SOAP (Simple Object Access Protocol)
	- SOAP is a protocol for exchanging structured information in the implementation of web services. It uses XML as the data interchange format and provides a standardized method for communication between different systems.


## Security Technologies

- Authentication and Authorization Mechanisms
	- Authentication verifies the identity of users, while authorization controls access to different parts of the web application based on user roles and permissions.
- Encryption (SSL/TLS)
	- SSL (Secure Socket Layer) or TLS (Transport Layer Security) is used to encrypt data transmitted between the client and server, ensuring secure communication and data protection.


## External Technologies

- Content Delivery Networks (CDNs)
	- CDNs are used to distribute static content (e.g., images, CSS files, JavaScript libraries) to multiple servers located worldwide, improving the web application's performance and reliability.
- Third-Party Libraries and Frameworks
	- Web applications often leverage third-party libraries and frameworks to speed up development and access advanced features.


## Web Application Architecture

![[Screenshot 2025-05-14 at 12.21.31.png]]


## How Web Pages are Rendered

![[Screenshot 2025-05-14 at 12.22.26.png]]


## How Web Browser Parse Responses

![[Screenshot 2025-05-14 at 12.23.46.png]]


#cybersecurity #eJPT 