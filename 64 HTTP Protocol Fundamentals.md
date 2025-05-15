# 64 HTTP Protocol Fundamentals

# Introduction to HTTP

- HTTP (Hypertext Transfer Protocol) is a stateless application layer protocol used for the transmission of resources like web application data and runs on top of TCP.
- It was specifically designed for communication between web browsers and web servers.
- HTTP utilizes the typical client-server architecture for communication, whereby the browser is the client, and the web server is the server.
- Resources are uniquely identified with a URL/URI.
- HTTP has 2 versions; HTTP 1.0 & HTTP 1.1.
	- HTTP 1.1 is the most widely used version of HTTP and has several advantages over HTTP 1.0 such as the ability to re-use the same connection and can request for multiple URI’s/Resources.


## HTTP Protocol Basics

- During HTTP communication, the client and the server exchange messages, typically classified as HTTP requests and responses.
- The client sends requests to the server and gets back responses.

![[Screenshot 2025-05-14 at 15.57.34.png]]


# HTTP Requests

## HTTP Request Components

**Request Line**

- The request line is the first line of an HTTP request and contains the following three components:
	- HTTP method (e.g., GET, POST, PUT, DELETE, etc.): Indicates the type of request being made.
	- URL (Uniform Resource Locator): The address of the resource the client wants to access.
	- HTTP version: The version of the HTTP protocol being used (e.g., HTTP/1.1).


**Request Headers**

- Headers provide additional information about the request. Common headers include:
	- User-Agent: Information about the client making the request (e.g., browser type).
	- Host: The hostname of the server.
	- Accept: The media types the client can handle in the response (e.g., HTML, JSON).
	- Authorization: Credentials for authentication, if required.
	- Cookie: Information stored on the client-side and sent back to the server with each request.


**Request Body (Optional)**

- Some HTTP methods (like POST or PUT) include a request body where data is sent to the server, typically in JSON or form data format.


## HTTP Request Example

- Let’s examine an HTTP request in detail. The following is the data contained in a request that we send when we navigate to www.google.com with a web browser.

 ```mermaid
graph LR
    Browser --> URL
    URL --> WebServer
```

```bash
GET / HTTP/1.1
Host: www.google.com
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:36.0)
Gecko/20100101 Firefox/36.0
Accept: text/html,application/xhtml+xml
Accept-Encoding: gzip, deflate
Connection: keep-alive
```


## HTTP Request Headers

- An HTTP request to www.google.com is initiated. What you see here are the headers (HTTP Request Headers) for this request.
- Note that a connection to www.google.com on port 80 is initiated before sending HTTP commands to the webserver.

```shell
GET / HTTP/1.1 # Request line
Host: www.google.com # HTTP Request Headers
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:36.0) # HTTP Request Headers
Gecko/20100101 Firefox/36.0 # HTTP Request Headers
Accept: text/html,application/xhtml+xml # HTTP Request Headers
Accept-Encoding: gzip, deflate # HTTP Request Headers
Connection: keep-alive # HTTP Request Headers
 
<BODY> # Request Body
```


## HTTP Request Methods

- HTTP request methods (HTTP Verbs) provide a standardized way for clients and servers to communicate and interact with resources on the web. The choice of the appropriate method depends on the type of operation that needs to be performed on the resource.
- GET is the default request method used when you make a request to a web application, in this case we are trying to connect to www.google.com.

```shell
GET / HTTP/1.1 # Request Method (GET)
Host: www.google.com
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64;
rv:36.0) Gecko/20100101 Firefox/36.0
Accept: text/html,application/xhtml+xml
Accept-Encoding: gzip, deflate
Connection: keep-alive
```


## HTTP Request Methods Explained

| Method  | Function |
|---------|----------|
| **GET** | The GET method is used to retrieve data from the server. It requests the resource specified in the URL and does not modify the server's state. It is a safe and idempotent method, meaning that making the same GET request multiple times should not have any side effects. |
| **POST** | The POST method is used to submit data to be processed by the server. It typically includes data in the request body, and the server may perform actions based on that data. POST requests can cause changes to the server's state, and they are not idempotent. |
| **PUT** | The PUT method is used to update or create a resource on the server at the specified URL. It replaces the entire resource with the new representation provided in the request body. If the resource does not exist, PUT can create it. |
| **DELETE** | The DELETE method is used to remove the resource specified by the URL from the server. After a successful DELETE request, the resource will no longer be available at that URL. |
| **PATCH** | The PATCH method is used to apply partial modifications to a resource. It is similar to the PUT method but only updates specific parts of the resource rather than replacing the entire resource. |
| **HEAD** | The HEAD method is similar to the GET method but only retrieves the response headers and not the response body. It is often used to check the headers for things like resource existence or modification dates. |
| **OPTIONS** | The OPTIONS method is used to retrieve information about the communication options available for the target resource. It allows clients to determine the supported methods and headers for a particular resource. |


## HTTP Request URL/Path

- The address of the resource/URI the client wants to access.
- The home page of a website is always "/". Other pages can be requested, of course, for example: /downloads/index.php.
- Your request always refers to the root folder to specify the requested file (hence the leading "/").

```shell
GET / HTTP/1.1 # URL/PATH (/)
Host: www.google.com
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64;
rv:36.0) Gecko/20100101 Firefox/36.0
Accept: text/html,application/xhtml+xml
Accept-Encoding: gzip, deflate
Connection: keep-alive
```


## HTTP Request Protocol

- This is the HTTP protocol version that your browser wants to communicate with (HTTP 1.0/HTTP 1.1)

```shell
GET / HTTP/1.1 # Protocol (HTTP/1.1)
Host: www.google.com
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64;
rv:36.0) Gecko/20100101 Firefox/36.0
Accept: text/html,application/xhtml+xml
Accept-Encoding: gzip, deflate
Connection: keep-alive
```


## HTTP Request Host Header

- This is the beginning of HTTP Request Headers. HTTP Headers have the following structure: Header-name:Header-Value.
- The Host header allows a web server to host multiple websites at a single IP address. Our browser is specifying in the Host header which website you are interested in.

```shell
GET / HTTP/1.1 
Host: www.google.com # Host Header
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64;
rv:36.0) Gecko/20100101 Firefox/36.0
Accept: text/html,application/xhtml+xml
Accept-Encoding: gzip, deflate
Connection: keep-alive
```

- After each request header, you will find its corresponding value. In this case we want to access the Host www.google.com.
- Note: Host value + Path combine to create the full URL you are requesting: the home page of www.google.com/


## HTTP Request User-Agent Header

- The User-Agent is used to specify and send your browser, browser version, operating system and language to the remote web server.
- All web browsers have their own user-agent identification string. This is how most web sites recognize the type of browser in use.

```shell
GET / HTTP/1.1 
Host: www.google.com 
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; # User-Agent Header
rv:36.0) Gecko/20100101 Firefox/36.0 # User-Agent Header
Accept: text/html,application/xhtml+xml
Accept-Encoding: gzip, deflate
Connection: keep-alive
```


## HTTP Request Accept Header

- The Accept header is used by your browser to specify which document/file types are expected to be returned from the web server as a result of this request.

```shell
GET / HTTP/1.1 
Host: www.google.com 
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; 
rv:36.0) Gecko/20100101 Firefox/36.0 
Accept: text/html,application/xhtml+xml # Accept Header
Accept-Encoding: gzip, deflate
Connection: keep-alive
```


## HTTP Request Accept-Encoding Header

- The Accept-Encoding header is similar to Accept, and is used to restrict the content encoding that is acceptable in the response.
- Content encoding is primarily used to allow a document to be compressed or transformed without losing the original format and without the loss of information.

```shell
GET / HTTP/1.1 
Host: www.google.com 
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64;
rv:36.0) Gecko/20100101 Firefox/36.0 
Accept: text/html,application/xhtml+xml
Accept-Encoding: gzip, deflate # Accept-Encoding Header
Connection: keep-alive
```


## HTTP Request Connection Header

- When using HTTP 1.1, you can maintain/re-use the connection to the remote web server for an unspecified amount of time using the value "keep-alive".
- This indicates that all requests to the web server will continue to be sent through this connection without initiating a new connection every time (as in HTTP 1.0).

```shell
GET / HTTP/1.1 
Host: www.google.com 
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; 
rv:36.0) Gecko/20100101 Firefox/36.0 
Accept: text/html,application/xhtml+xml
Accept-Encoding: gzip, deflate
Connection: keep-alive # Connection Header
```


# HTTP Responses

## HTTP Response Components

**Response Headers**

- Similar to request headers, response headers provide additional information about the response. Common headers include:
	- Content-Type: The media type of the response content (e.g., text/html, application/json).
	- Content-Length: The size of the response body in bytes.
	- Set-Cookie: Used to set cookies on the client-side for subsequent requests
	- Cache-Control: Directives for caching behavior.

**Response Body (Optional)**

- The response body contains the actual content of the response. For example, in the case of an HTML page, he response body will contain the HTML markup.


## HTTP Request Response Example

- Now that we know what an HTTP request comprises of, let us inspect HTTP responses.

 ```mermaid
graph LR
    WebServer --> URL
    URL --> Browser
```

- In response to the HTTP Request, the web server will respond with the requested resource, preceded by a bunch of new HTTP response headers.
- These new response headers from the web server will be used by your web browser to interpret the content contained in the Response content/body of the response.


## HTTP Response Example

- The code snipper below is an example of a typical web server response.
- Note: The body of the response/page content has been omitted as it is not relevant at this point in time.
- Let us inspect some of these HTTP response headers in greater detail.

```shell
HTTP/1.1 200 OK
Date: Fri, 13 Mar 2015 11:26:05 GMT
Cache-Control: private, max-age=0
Content-Type: text/html; charset=UTF-8
Content-Encoding: gzip
Server: gws
Content-Length: 258

<PAGE CONTENT>
```


## HTTP Response Status-Line

- The first line of an HTTP Response is the Status-Line, consisting of the protocol version (HTTP 1.1) followed by the HTTP status code (200) and its relative textual meaning (OK).

```shell
HTTP/1.1 200 OK # Status-line Header
Date: Fri, 13 Mar 2015 11:26:05 GMT
Cache-Control: private, max-age=0
Content-Type: text/html; charset=UTF-8
Content-Encoding: gzip
Server: gws
Content-Length: 258

<PAGE CONTENT>
```


## Common HTTP Status Codes

| Status Code                   | Meaning                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **200 OK**                    | The request was successful, and the server has returned the requested data.                                                                                               |
| **301 Moved Permanently**     | The requested resource has been permanently moved to a new URL, and the client should use the new URL for all future requests.                                            |
| **302 Found**                 | The requested resource is temporarily located at a different URL. This code is commonly used for temporary redirections, but it's often better to use 303 or 307 instead. |
| **400 Bad Request**           | The server cannot process the request due to a client error (e.g., malformed request syntax).                                                                             |
| **401 Unauthorized**          | Authentication is required, and the client must provide valid credentials to access the requested resource.                                                               |
| **403 Forbidden**             | The server understood the request, but the client does not have permission to access the requested resource.                                                              |
| **404 Not Found**             | The requested resource could not be found on the server.                                                                                                                  |
| **500 Internal Server Error** | The server encountered an error while processing the request, and the specific cause is not provided.                                                                     |


## HTTP Response Date Header

- The "Date" header in an HTTP response is used to indicate the date and time when the response was generated by the server.
- It helps clients and intermediaries to understand the freshness of the response and to synchronize the time between the server and the client.

```shell
HTTP/1.1 200 OK 
Date: Fri, 13 Mar 2015 11:26:05 GMT # Date Header
Cache-Control: private, max-age=0
Content-Type: text/html; charset=UTF-8
Content-Encoding: gzip
Server: gws
Content-Length: 258

<PAGE CONTENT>
```


## HTTP Response Cache-Control Header

- The Cache headers allow the Browser and the Server to agree about caching rules. It allow web servers to instruct clients on how long they can cache the response and under what conditions they should revalidate it with the server.
- This helps in optimizing the performance and efficiency of web applications by reducing unnecessary network requests. 

```shell
HTTP/1.1 200 OK 
Date: Fri, 13 Mar 2015 11:26:05 GMT
Cache-Control: private, max-age=0 # Cache-Control Header
Content-Type: text/html; charset=UTF-8
Content-Encoding: gzip
Server: gws
Content-Length: 258

<PAGE CONTENT>
```


## Cache-Control Directives

| Directive                   | Meaning                                                                                                                                                         |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Public**                  | Indicates that the response can be cached by any intermediary caches (such as proxy servers) and shared across different users.                                 |
| **Private**                 | Specifies that the response is intended for a specific user and should not be cached by intermediate caches.                                                    |
| **no-cache**                | Instructs the client to revalidate the response with the server before using the cached version. It does not prevent caching but requires revalidation.         |
| **no-store**                | Directs the client and intermediate caches not to store any version of the response. It ensures that the response is not cached in any form.                    |
| **max-age=&lt;SECONDS&gt;** | Specifies the maximum amount of time in seconds that the response can be cached by the client. After this period, the client should revalidate with the server. |


## HTTP Response Content-Type Header

- The "Content-Type" header in an HTTP response is used to indicate the media type of the response content.
- It tells the client what type of data the server is sending so that the client can handle it appropriately.

```shell
HTTP/1.1 200 OK 
Date: Fri, 13 Mar 2015 11:26:05 GMT
Cache-Control: private, max-age=0 
Content-Type: text/html; charset=UTF-8 # Content-Type Header
Content-Encoding: gzip
Server: gws
Content-Length: 258

<PAGE CONTENT>
```


## HTTP Response Content-Encoding Header

 - The "Content-Encoding" header in an HTTP response is used to specify the compression encoding applied to the response content.
 - It tells the client how the server has encoded the response data, allowing the client to decode and decompress the data correctly.

```shell
HTTP/1.1 200 OK 
Date: Fri, 13 Mar 2015 11:26:05 GMT
Cache-Control: private, max-age=0 
Content-Type: text/html; charset=UTF-8 
Content-Encoding: gzip # Content-Encoding Header
Server: gws
Content-Length: 258

<PAGE CONTENT>
```


## HTTP Response Server Header

- The Server header displays the Web Server banner, for example, Apache, Nginx, IIS etc.
- Google uses a custom web server banner: gws (Google Web Server).

```shell
HTTP/1.1 200 OK 
Date: Fri, 13 Mar 2015 11:26:05 GMT
Cache-Control: private, max-age=0 
Content-Type: text/html; charset=UTF-8 
Content-Encoding: gzip
Server: gws # Server Header
Content-Length: 258

<PAGE CONTENT>
```


# HTTP Basics Lab

```shell
# Packet capture
wireshark -i <interface>

# Active Internet connections (servers and established)
netstat -antp

# See header and source code
curl -v <ip>
curl -v -I <ip> # Use HEAD HTTP Request Method
curl -v -X PUT <ip> # Use PUT HTTP Request Method
curl -v -X OPTIONS <ip> # Available HTTP Request Method
curl <ip> --upload-file <file> # If PUT it available
```


# HTTPS

- Now that you have an understanding of how HTTP works, let us explore how it is secured/protected.
- By default, HTTP requests are sent in clear-text and can be easily intercepted or mangled by an attacker on the way to its destination.
- Moreover, HTTP does not provide strong authentication between the two communicating parties.
- HTTPS (Hypertext Transfer Protocol Secure) is a secure version of the HTTP protocol, which is used to transmit data between a user's web browser and a website or web application.
- HTTPS provides an added layer of security by encrypting the data transmitted over the internet, making it more secure and protecting it from authorized access and interception.
- HTTPS is also commonly referred to as HTTP Secure.
- HTTPS is the preferred way to use and configure HTTP and involves running HTTP over SSL/TLS.
- SSL (Secure Sockets Layer) and TLS (Transport Layer Security) are cryptographic protocols used to provide secure communication over a computer network, most commonly the internet.
- They are essential for establishing a secure and encrypted connection between a user's web browser or application and a web server. 
- This layering techniques provides confidentiality, integrity protection and authentication to the HTTP protocol. 


## HTTPS Advantages 

- Encryption of Data in Transit
	- One of the primary benefits of HTTPS is data encryption during transmission. When data is sent over an HTTPS connection, it is encrypted using strong cryptographic algorithms. This ensurer that even if an attacker intercepts the data while it's in transit, they cannot decipher or read its contents.
- Protection Against Eavesdropping
	- HTTPS prevents unauthorized parties from eavesdropping on the data exchanged between the user's browser and the web server. This is particularly crucial when users input sensitive information, such as login credentials, credit card numbers, or personal details. 


## HTTPS Security Considerations

- HTTPS does not protect against web application flaws! Various web application attacks will still work regardless of the use of SSL/TLS. (Attacks like XSS and SQLi will still work).
- The added encryption layer only protects data exchanged between the client and the server and does stop attacks against the web application itself. 


#cybersecurity #eJPT 