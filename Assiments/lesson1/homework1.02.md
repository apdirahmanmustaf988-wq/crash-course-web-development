# The Journey of a URL: From Browser to Webpage

When you type a URL such as `https://www.example.com` into a web browser and press **Enter**, many different processes happen behind the scenes before the webpage appears on your screen. The browser, DNS servers, network protocols, web servers, and rendering engines all work together to deliver the page.

## 1. Entering the URL

The journey begins when you type a URL into the browser's address bar.

For example:

```text
https://www.example.com/products
```

A URL contains several important components:

- **HTTPS** — the protocol used to communicate securely.
- **www.example.com** — the domain name.
- **/products** — the specific resource or path requested from the server.

The browser first analyzes the URL to determine where and how the request should be sent.

## 2. Checking the Browser Cache

Before contacting the internet, the browser may check whether it already has information about the website stored locally.

It can check:

- Browser cache
- Previously stored DNS information
- Cookies
- Cached webpage resources

If the browser already has a valid copy of some resources, it may reuse them instead of downloading everything again.

If it needs the server's IP address, it proceeds with DNS resolution.

## 3. DNS Lookup

Humans normally use domain names such as:

```text
www.example.com
```

Computers communicate using IP addresses such as:

```text
93.184.216.34
```

The **Domain Name System (DNS)** translates the domain name into an IP address.

The browser or operating system may first check its local DNS cache. If the address is not available, a DNS query is sent to a DNS resolver, often provided by an internet service provider or another DNS service.

The resolver may contact other DNS servers to find the answer.

A simplified process looks like this:

```text
Browser
   ↓
Operating System
   ↓
DNS Resolver
   ↓
Root DNS Server
   ↓
.com DNS Server
   ↓
Authoritative DNS Server
   ↓
IP Address
```

The final result tells the browser which IP address belongs to the requested domain.

## 4. Establishing a Network Connection

Once the browser knows the server's IP address, it needs to establish a connection.

For HTTPS websites, modern browsers commonly use **TCP with TLS** for HTTP/1.1 or HTTP/2, while HTTP/3 uses **QUIC over UDP**.

For a traditional HTTPS connection using TCP, the process starts with the **TCP three-way handshake**:

```text
Client → Server: SYN
Client ← Server: SYN-ACK
Client → Server: ACK
```

This establishes a reliable connection between the browser and server.

## 5. TLS Security Handshake

Because the URL uses HTTPS, the connection must also be secured using **TLS (Transport Layer Security)**.

During the TLS handshake, the browser and server negotiate security settings and establish encryption keys.

The browser also verifies the website's digital certificate to help confirm that it is communicating with the intended website.

After successful negotiation, data sent between the browser and server is encrypted.

So instead of sending webpage information as ordinary readable data, it travels through an encrypted connection.

## 6. Sending the HTTP Request

The browser can now send an HTTP request to the web server.

For example, a simplified request might look like:

```http
GET /products HTTP/2
Host: www.example.com
```

The request tells the server:

> "I want the `/products` resource from `www.example.com`."

The browser may also send additional information, such as:

- Cookies
- Accepted content types
- Language preferences
- Browser information
- Authentication information, when applicable

## 7. The Request Travels Across the Internet

The request does not travel directly from your computer to the web server in one step.

It passes through multiple network devices, such as:

```text
Your Computer
      ↓
Wi-Fi Router
      ↓
Internet Service Provider
      ↓
Internet Routers
      ↓
Web Server
```

Routers examine the destination IP address and forward packets toward the appropriate network.

The internet is essentially a huge interconnected collection of networks that work together to deliver the data.

## 8. The Web Server Receives the Request

Eventually, the request reaches the server responsible for the website.

The server may be running software such as a web server or application server.

Examples include:

- Nginx
- Apache
- Microsoft IIS

The server examines the request and determines what response should be returned.

For a simple static webpage, it might retrieve an HTML file.

For a dynamic website, the request might be passed to application code.

## 9. Backend Processing

If the requested page is dynamic, the backend may perform several operations.

For example, an online shopping website might:

```text
Browser
   ↓
Web Server
   ↓
Backend Application
   ↓
Database
   ↓
Backend Application
   ↓
Web Server
```

The backend could:

- Check the user's account
- Retrieve products
- Query a database
- Calculate information
- Process authentication
- Generate HTML or JSON data

The database stores information that the application needs.

For example:

```text
Products
Users
Orders
Prices
Categories
```

Once processing is complete, the server prepares a response.

## 10. The Server Sends an HTTP Response

The server sends an HTTP response back to the browser.

A simplified response might look like:

```http
HTTP/2 200 OK
Content-Type: text/html
```

Then the server sends the HTML content.

The status code tells the browser what happened.

For example:

- **200 OK** — request succeeded
- **301/302** — redirect
- **404 Not Found** — requested resource could not be found
- **500 Internal Server Error** — server encountered an error

## 11. The Browser Receives the HTML

The browser now receives the webpage's HTML.

For example:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Website</title>
</head>
<body>
    <h1>Welcome!</h1>
    <p>Hello, world!</p>
</body>
</html>
```

However, receiving the HTML does **not** mean the webpage is finished.

The browser must interpret the HTML and find the other resources required by the page.

## 12. The Browser Finds CSS, JavaScript, and Images

While reading the HTML, the browser may discover references to other files.

For example:

```html
<link rel="stylesheet" href="style.css">

<script src="script.js"></script>

<img src="image.jpg">
```

The browser then requests these resources from the server.

This can result in additional network requests for:

- CSS files
- JavaScript files
- Images
- Fonts
- Videos
- Other webpage resources

Some resources may already be stored in the browser cache, so they might not need to be downloaded again.

## 13. HTML Becomes the DOM

The browser's rendering engine parses the HTML and constructs a structure called the **DOM (Document Object Model)**.

For example:

```html
<body>
    <h1>Hello</h1>
    <p>Welcome to my website.</p>
</body>
```

Can be represented conceptually as:

```text
Document
 └── body
      ├── h1
      │    └── "Hello"
      └── p
           └── "Welcome to my website."
```

The DOM represents the structure and content of the webpage.

## 14. CSS Becomes the CSSOM

The browser also processes CSS.

For example:

```css
h1 {
    color: blue;
    font-size: 32px;
}
```

The browser creates a structure called the **CSSOM (CSS Object Model)**, representing the styles that should be applied to the document.

The browser combines information from the DOM and CSSOM to determine how elements should appear.

## 15. JavaScript Is Executed

If the webpage contains JavaScript, the browser's JavaScript engine executes it.

JavaScript can:

- Change webpage content
- Respond to button clicks
- Validate forms
- Request additional data
- Modify CSS
- Create animations
- Update the DOM

For example:

```javascript
document.querySelector("h1").textContent = "Welcome!";
```

This changes the content of the heading after the JavaScript runs.

## 16. Building the Render Tree

The browser combines the DOM and CSS information to create a **render tree**.

The render tree contains the elements that need to be displayed and the information necessary to display them.

Some elements, such as elements hidden with CSS, may not appear in the render tree.

## 17. Layout

Next, the browser calculates the position and size of each visible element.

This process is called **layout**.

The browser determines things such as:

- Width
- Height
- Position
- Margins
- Padding
- Text placement
- Element relationships

For example:

```text
Header
 ├── Logo
 └── Navigation

Main
 ├── Heading
 ├── Paragraph
 └── Image

Footer
```

The browser calculates where each part should appear on the screen.

## 18. Painting the Page

After calculating the layout, the browser begins **painting** the page.

It determines what should actually be drawn, including:

- Text
- Colors
- Borders
- Backgrounds
- Images
- Shadows
- Other visual elements

The browser converts the webpage's instructions into graphical information that can be displayed.

## 19. Compositing

Modern browsers may divide the page into different layers.

These layers can then be combined, or **composited**, to produce the final image.

This is particularly useful for things such as:

- Animations
- Transforms
- Scrolling
- Video
- Fixed elements

The browser may use the computer's GPU to help efficiently render certain visual operations.

## 20. The Page Appears on the Screen

Finally, the browser displays the rendered webpage on your screen.

The complete journey can be summarized as:

```text
Enter URL
    ↓
Parse URL
    ↓
Check Cache
    ↓
DNS Lookup
    ↓
Get IP Address
    ↓
Establish Network Connection
    ↓
TLS Handshake
    ↓
Send HTTP Request
    ↓
Server Receives Request
    ↓
Backend / Database Processing
    ↓
HTTP Response
    ↓
Receive HTML
    ↓
Download CSS / JS / Images
    ↓
Build DOM
    ↓
Build CSSOM
    ↓
Execute JavaScript
    ↓
Build Render Tree
    ↓
Layout
    ↓
Paint
    ↓
Composite
    ↓
Webpage Appears
```

## Conclusion

Entering a URL looks like a simple action, but it starts a complex chain of processes. **DNS** finds the server's IP address, **network protocols** deliver the request, **TLS** protects HTTPS communication, **HTTP** transfers resources, the **server and backend** process the request, and finally the browser's **rendering engine** transforms HTML, CSS, and JavaScript into the webpage you see.

This entire process usually happens extremely quickly, often within a fraction of a second or a few seconds depending on the network, server, and complexity of the page.
