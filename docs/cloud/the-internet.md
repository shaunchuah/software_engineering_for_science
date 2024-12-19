# The Internet

Before we proceed any further, it would be helpful to revisit the basics of the internet. This will help you understand what happens when calling APIs as well as connecting to remote servers.

## What is the Internet?

The internet is a global network of computers that are connected to each other. It allows computers to communicate with each other and share information. The internet is made up of a collection of networks that are connected using a set of standard protocols.

## The TCP/IP Protocol

TCP/IP (Transmission Control Protocol/Internet Protocol) is the foundational suite of communication protocols used for interconnecting network devices on the internet and most private networks. It dictates how data should be packetized, addressed, transmitted, routed, and received. TCP/IP is a layered protocol suite, primarily composed of four abstraction layers.

### 1. Application Layer

Provides protocols that applications use to communicate across the network.

Common protocols: HTTP, HTTPS, FTP, SMTP, IMAP, and DNS.

This layer interfaces directly with end-user software applications, ensuring data is properly packaged and formatted for delivery.

### 2. Transport Layer

Manages end-to-end communication, providing reliable data transfer and error checking.

Primary protocols:

- TCP (Transmission Control Protocol): Ensures reliable, ordered, and error-checked delivery of data between applications. It establishes a connection-oriented communication session.
- UDP (User Datagram Protocol): Provides a faster, connectionless service, useful for applications where speed is critical, and error correction is handled by the application itself, such as video streaming or online gaming.

### 3. Internet Layer

Handles the logical addressing, routing, and delivery of packets across the network.

Key protocol: IP (Internet Protocol):

- IPv4: Uses 32-bit addresses, limiting the address space to about 4.3 billion unique addresses.
- IPv6: Uses 128-bit addresses, vastly expanding the address space and addressing limitations of IPv4.

### 4. Link Layer

Also known as the Network Interface Layer, it encompasses the protocols and hardware required to transmit data across physical network segments. Responsible for managing hardware addressing and the physical transmission of data. Includes technologies like Ethernet, Wi-Fi, and other data link technologies.

### How TCP/IP Works

1. Application Layer: A user application (e.g., web browser) initiates communication and generates data, which is then passed to the transport layer.
2. Transport Layer: The data is segmented into smaller chunks. In this case, TCP is used and a connection is established with the receiving end, segments are numbered, and a checksum is calculated for error detection.
3. Internet Layer: The transport layer segments are encapsulated into IP packets. Each packet is assigned a source and destination IP address, routing it through the network.
4. Link Layer: The IP packets are framed into link-layer frames, which include MAC addresses. These frames are transmitted over the physical network media.
5. Receiving End: At the destination, the process reverses. The link layer frames are unpacked to retrieve the IP packets, which are then passed to the transport layer. The transport layer reassembles the segments and hands the data off to the application layer.

## What is a URL?

A URL (Uniform Resource Locator) is an address used to access resources on the internet. It consists of several parts:

1. Scheme: Indicates the protocol (e.g., http, https).
2. Host: Specifies the domain name or IP address (e.g., <www.example.com>).
3. Port (optional): Defines the port number (e.g., :8080).
4. Path: Shows the location of the resource on the server (e.g., /docs/search).
5. Query (optional): Contains parameters for searching or filtering (e.g., ?q=test).
6. Fragment (optional): Points to a specific section within the resource (e.g., #part2).

URLs are essential for uniquely identifying and retrieving resources on the web.

## The HTTP Protocol

HTTP (Hypertext Transfer Protocol) is an application-layer protocol used primarily for transmitting hypermedia documents, such as HTML. It is the foundation of any data exchange on the Web and is a protocol used by web browsers and web servers to communicate.

### Key Features of HTTP

1. Client-Server Model: HTTP operates based on a client-server model. A client, typically a web browser, sends a request to a server, which then processes the request and sends back the appropriate response.
2. Stateless Protocol: HTTP is a stateless protocol, meaning each request from a client to a server is independent. The server does not retain any session information between different requests from the same client.
3. Methods (Verbs): HTTP defines several methods that indicate the desired action to be performed on a resource. The most common methods are:
    - GET: Retrieve data from the server (e.g., fetch a web page).
    - POST: Send data to the server (e.g., submit form data).
    - PUT: Update or create a resource on the server.
    - DELETE: Remove a resource from the server.
    - HEAD: Retrieve metadata about the resource without fetching the actual resource.
    - OPTIONS: Describe the communication options for the target resource.
4. Headers: HTTP requests and responses include headers, which provide additional information about the request or the response. Common headers include:
    - Content-Type: Indicates the media type of the resource.
    - User-Agent: Provides information about the client software.
    - Accept: Specifies the media types that the client is willing to receive.
    - Authorization: Contains credentials for authenticating the client.
    - Host: Indicates the domain name of the server (for virtual hosting).
5. Status Codes: HTTP responses include status codes that indicate the result of the request. Example of status codes are:
    - **2xx Success Codes**
        - 200 OK: The request was successful.
    - **3xx Redirection**
        - 301 Moved Permanently: The resource has been moved permanently to a new location.
    - **4xx Client Errors**
        - 400 Bad Request: The request could not be understood by the server due to malformed syntax.
        - 403 Forbidden: The server understood the request but refuses to authorize it.
        - 404 Not Found: The requested resource could not be found.
    - **5xx Server Errors**
        - 500 Internal Server Error: An error occurred on the server.

### How HTTP Works

1. Client Initiates Request: The client, such as a web browser, sends an HTTP request to a server. This request includes a request line (method, URI, HTTP version), headers, and possibly a body.

2. Server Processes Request: The server receives the request, processes it, and performs the desired action (e.g., fetching a resource, processing data).

3. Server Sends Response: After processing the request, the server sends an HTTP response back to the client. The response includes a status line (HTTP version, status code, reason phrase), headers, and possibly a body (e.g., the requested web page).

4. Client Receives and Processes Response: The client receives the response and processes it accordingly. For example, a web browser might render the HTML content received from the server.
