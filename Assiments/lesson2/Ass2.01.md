# URL Breakdown

## Example URL

`https://www.example.com/products/laptops/index.html?id=25#reviews`

### URL Components

  ---------------------------------------------------------------------------------------
  Component               Value                            Description
  ----------------------- -------------------------------- ------------------------------
  **Protocol (Scheme)**   `https`                          Defines how the browser
                                                           communicates with the server
                                                           securely.

  **Subdomain**           `www`                            Identifies a specific section
                                                           of the website.

  **Domain Name**         `example`                        The main name of the website.

  **Top-Level Domain      `.com`                           Indicates the type of domain.
  (TLD)**                                                  

  **Path**                `/products/laptops/index.html`   Specifies the location of the
                                                           requested resource on the
                                                           server.

  **Query String**        `?id=25`                         Sends additional information
                                                           (parameters) to the server.

  **Fragment (Anchor)**   `#reviews`                       Takes the browser to a
                                                           specific section of the
                                                           webpage.
  ---------------------------------------------------------------------------------------

------------------------------------------------------------------------

# Role-Play the Request--Response Cycle

## Correct Order

1.  **User**
    -   Types a website address (URL) into the browser.
2.  **Browser**
    -   Sends a request to the **DNS Server** to find the website's IP
        address.
3.  **DNS Server**
    -   Looks up the IP address and returns it to the browser.
4.  **Browser**
    -   Sends an **HTTP/HTTPS request** to the **Web Server** using the
        IP address.
5.  **Web Server**
    -   Processes the request and sends the requested webpage (HTML,
        CSS, JavaScript, images, etc.) back to the browser.
6.  **Browser**
    -   Displays the webpage to the user.

## Request--Response Flow

``` text
User
  │
  ▼
Browser
  │
  ▼
DNS Server (Finds IP Address)
  │
  ▼
Browser
  │
  ▼
Web Server
  │
  ▼
Browser
  │
  ▼
User Sees the Webpage
```
