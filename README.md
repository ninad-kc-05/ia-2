# CN IA 2 solns

## Study priority

1.  **Module V --- Application Layer and Network Services** (7 marks per
    question)
2.  **Module VI --- Emerging Network Technologies and Security** (7
    marks per question)
3.  **Module IV --- Transport Layer Protocols** (2 marks per question)


------------------------------------------------------------------------

# Priority 1 --- Module V: Application Layer and Network Services

## Q1. Analyze the client-server paradigm and explain how the client and server coordinate to provide a network service.

The **client-server paradigm** is a network architecture in which a
client requests a service or resource and a server receives the request,
processes it, and returns a response.

### Working

1.  The **server starts** and listens for requests at a known network
    address and port.
2.  The **client initiates communication** by sending a request to the
    server.
3.  The server receives and interprets the request.
4.  The server performs the required operation---for example, retrieving
    a webpage or looking up a record.
5.  The server sends a response containing the result or an error.
6.  The client processes and displays the response. The exchange may
    repeat for further requests.

### Example

When a user opens a website, the browser acts as the client. It sends an
HTTP request to the web server. The server processes the request and
returns an HTTP response containing the requested page or a status/error
message.

### Advantages

-   Centralized management of data and services.
-   Easier maintenance and updating on the server.
-   Multiple clients can use the same service.
-   Access control and backups can be managed centrally.

### Limitations

-   A server failure can interrupt service for its clients.
-   The server may become a performance bottleneck under heavy load.
-   The network connection affects response time.

**Diagram to study:** ### Client-Server Architecture Diagram

![Many-to-Many Client-Server Relationship](https://www.cloudflare.com/img/learning/serverless/glossary/client-side-vs-server-side/many-to-many-client-server-relationship.svg)

*Figure: Many-to-many relationship between clients and servers. Source: Cloudflare.*

------------------------------------------------------------------------

## Q2. Compare and analyze FTP and HTTP with respect to their purpose, communication mechanism, and typical applications.

**FTP (File Transfer Protocol)** is designed for transferring files
between systems. **HTTP (Hypertext Transfer Protocol)** is designed for
transferring web resources and is the foundation of communication
between web clients and servers.

  -----------------------------------------------------------------------
  Feature                 FTP                     HTTP
  ----------------------- ----------------------- -----------------------
  Main purpose            Uploading and           Requesting and
                          downloading files       transferring web
                                                  resources

  Communication model     Client-server;          Request-response
                          traditionally uses      between client and
                          separate control and    server
                          data connections        

  Typical use             File repositories and   Web pages, web APIs,
                          managed file transfers  images and other web
                                                  resources

  Authentication          May use user            May use cookies,
                          credentials; secure     tokens, or other
                          variants are preferable authentication
                                                  mechanisms

  Security                Plain FTP does not      HTTPS protects HTTP
                          encrypt traffic; FTPS   using TLS
                          adds TLS                

  Common ports            TCP 21 for FTP control; TCP 80 for HTTP and TCP
                          data connection depends 443 for HTTPS by
                          on mode                 convention
  -----------------------------------------------------------------------

### Analysis

FTP is suited to moving files, especially when the client needs
file-management operations. HTTP is suited to delivering linked
resources and powering websites and web APIs. FTP and HTTP are not
interchangeable: their commands, semantics, and typical uses differ.

**Important distinction:** SFTP is an SSH-based file-transfer protocol;
it is not simply "secure FTP." FTPS is FTP protected with TLS.

**Diagram/reference:** [MDN --- Overview of
HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview)

------------------------------------------------------------------------

## Q3. Compare and analyze two different APIs used for accessing network services based on their communication mechanism and functionality.

An **API (Application Programming Interface)** provides defined
operations that a program can use to communicate with another program or
service. The question does not specify which two APIs are expected. The
following is an illustrative comparison of the **Berkeley sockets API**
and the **HTTP Fetch API**.

  -----------------------------------------------------------------------
  Feature                 Berkeley sockets API    HTTP Fetch API
  ----------------------- ----------------------- -----------------------
  Main purpose            Provides low-level      Allows web applications
                          network communication   to make HTTP requests
                          endpoints               

  Communication           Can support TCP streams Sends HTTP requests and
                          or UDP datagrams, among exposes responses to
                          other socket types      application code

  Level of abstraction    Lower-level; the        Higher-level; HTTP
                          programmer manages      methods, headers,
                          connection and          bodies and responses
                          data-transfer details   are represented by web
                                                  APIs

  Typical operations      `socket()`, `bind()`,   `fetch()`, followed by
                          `listen()`, `accept()`, handling the returned
                          `connect()`, `send()`   `Response`
                          and `recv()`            

  Typical use             Network servers,        Browser applications
                          clients and             and web requests
                          system-level            
                          applications            

  Control                 Greater control over    Convenient for
                          transport-level         HTTP-based services but
                          communication           subject to browser
                                                  security rules
  -----------------------------------------------------------------------

### Analysis

Sockets are appropriate when an application needs direct control over
TCP or UDP communication. Fetch is appropriate when a web application
needs to request resources from an HTTP service without implementing the
transport protocol itself.

**Example** - A TCP server uses `socket()`, `bind()`, and `listen()` to
prepare for connections. - A browser application can call
`fetch("https://example.com/data")` to request an HTTP resource.

**References:** [Python socket
documentation](https://docs.python.org/3/library/socket.html) · [MDN ---
Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

**Check your class notes:** If your instructor specifies a different
pair of APIs, use that pair in the final exam answer.

------------------------------------------------------------------------

## Q4. Compare and analyze HTTP request and HTTP response messages with respect to their structure and purpose.

HTTP uses a **request-response model**. The client sends a request
asking the server to perform an operation; the server returns a response
describing the result.

### Structure of an HTTP request

1.  **Request line:** method, resource path and HTTP version. Example:
    `GET /index.html HTTP/1.1`
2.  **Headers:** metadata such as `Host`, `Accept` and `Authorization`.
3.  **Blank line:** separates headers from the body.
4.  **Optional body:** data sent with methods such as `POST` or `PUT`.

### Structure of an HTTP response

1.  **Status line:** HTTP version, status code and reason phrase.
    Example: `HTTP/1.1 200 OK`
2.  **Headers:** metadata such as `Content-Type` and `Content-Length`.
3.  **Blank line:** separates headers from the body.
4.  **Optional body:** the returned webpage, data, or error details.

  -----------------------------------------------------------------------------
  Feature                 HTTP request            HTTP response
  ----------------------- ----------------------- -----------------------------
  Direction               Client to server        Server to client

  Start line              Method, target and      Version, status code and
                          version                 reason phrase

  Purpose                 Requests an action or   Reports the outcome and may
                          resource                return the resource

  Examples                `GET`, `POST`, `PUT`,   `200 OK`, `404 Not Found`,
                          `DELETE`                `500 Internal Server Error`

  Body                    Optional; often         Optional; often contains
                          contains submitted data returned data
  -----------------------------------------------------------------------------

### Example exchange

``` http
GET /index.html HTTP/1.1
Host: example.com
Accept: text/html
```

``` http
HTTP/1.1 200 OK
Content-Type: text/html

<h1>Welcome</h1>
```

**Diagram:** [MDN --- HTTP messages, with request and response
diagrams](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Messages)

------------------------------------------------------------------------

# Priority 2 --- Module VI: Emerging Network Technologies and Security

## Q1. Analyze the working of MPLS and explain how labels are used to forward packets through the network.

**MPLS (Multiprotocol Label Switching)** forwards packets using short
labels rather than requiring every core router to make a forwarding
decision from the full network-layer header at each hop. It is often
described as operating between traditional Layer 2 forwarding and Layer
3 routing.

### Main components

-   **Label Edge Router (LER):** adds a label as traffic enters an MPLS
    domain and removes it as traffic leaves.
-   **Label Switching Router (LSR):** forwards labelled packets within
    the MPLS domain.
-   **Label-Switched Path (LSP):** the path followed by labelled packets
    through the MPLS network.
-   **Label:** a locally meaningful identifier associated with a
    forwarding class.

### Working

1.  The ingress LER examines an incoming packet and classifies it into a
    forwarding equivalence class.
2.  It **pushes** an MPLS label onto the packet.
3.  Each intermediate LSR checks the incoming label against its
    label-forwarding table.
4.  The LSR normally **swaps** the incoming label for an outgoing label
    and forwards the packet to the next hop.
5.  The egress LER, or in some designs the penultimate router, **pops**
    the label.
6.  The packet continues toward its destination.

### Advantages

-   Efficient forwarding through the MPLS core.
-   Supports traffic engineering and managed paths.
-   Can support VPN services and QoS policies.
-   Can carry different network-layer traffic.

### Limitation

MPLS requires additional configuration and operational expertise; its
benefits depend on the network design.

**Diagram/reference:** [Cisco --- MPLS label and forwarding
overview](https://www.cisco.com/c/en/us/support/docs/multiprotocol-label-switching-mpls/mpls/4649-mpls-faq-4649.html)

------------------------------------------------------------------------

## Q2. Analyze the spectrum requirements of 5G networks and explain why different frequency bands are required.

5G needs radio spectrum that can support **wide coverage, high data
rates, high capacity, and low-latency services**. No single frequency
band optimizes all these goals, so networks use different bands for
different conditions.

### Why different bands are needed

-   **Low-band spectrum:** radio signals generally travel farther and
    penetrate buildings better. It is useful for broad geographic
    coverage, including rural areas, but typically offers less bandwidth
    and lower peak capacity.
-   **Mid-band spectrum:** provides a balance between coverage and
    capacity. It is widely useful for urban and suburban 5G deployments.
-   **High-band/mmWave spectrum:** offers large amounts of bandwidth and
    very high data rates, but has shorter range and is more easily
    blocked by walls, buildings, and obstacles. It often requires denser
    deployments.

### Other requirements

-   Sufficient contiguous bandwidth for high throughput.
-   Capacity to serve many connected devices.
-   Efficient spectrum reuse in dense areas.
-   Coordination with existing spectrum users and other radio systems.
-   Suitable deployment choices based on terrain, buildings, and traffic
    demand.

### Conclusion

A layered spectrum strategy combines low-band coverage, mid-band
capacity, and high-band peak performance. Operators can select or
combine bands according to local coverage and capacity needs.

**Diagram/reference:** [U.S. FCC --- Making Spectrum Available (low-,
mid- and high-band
overview)](https://docs.fcc.gov/public/attachments/DOC-369307A2.pdf)

------------------------------------------------------------------------

## Q3. Analyze different types of cybercrime and identify the vulnerabilities that can be exploited in each case.

**Cybercrime** refers to unlawful activity in which computers, networks,
or digital systems are the target or tool of the offence.

  -----------------------------------------------------------------------
  Type of cybercrime      What it involves        Example vulnerability
                                                  exploited
  ----------------------- ----------------------- -----------------------
  Phishing and online     Deceiving people into   Weak verification of
  fraud                   revealing information   messages, poor
                          or making payments      awareness, or stolen
                                                  credentials

  Unauthorized access     Accessing accounts or   Weak/reused passwords,
                          systems without         missing multi-factor
                          permission              authentication,
                                                  unpatched software

  Malware and ransomware  Installing malicious    Unsafe downloads,
                          software, potentially   vulnerable software,
                          encrypting or stealing  excessive privileges
                          data                    

  Identity theft          Misusing personal       Data leaks, exposed
                          information to          personal details, weak
                          impersonate someone     account security

  Denial-of-service       Overwhelming a service  Insufficient capacity
  attacks                 so legitimate users     or inadequate traffic
                          cannot access it        filtering and rate
                                                  controls

  Web application attacks Abusing a website or    Input-validation flaws,
                          application to access   injection
                          or alter data           vulnerabilities, broken
                                                  access control

  Data theft or leakage   Obtaining confidential  Misconfigured storage,
                          information without     excessive permissions,
                          authorization           poor encryption or
                                                  monitoring
  -----------------------------------------------------------------------

### Prevention

-   Use unique, strong passwords and multi-factor authentication.
-   Apply security updates promptly.
-   Verify links, attachments and requests for sensitive information.
-   Limit user privileges and secure access permissions.
-   Maintain offline or otherwise protected backups.
-   Use encryption, logging, monitoring and incident-response
    procedures.
-   Provide regular security-awareness training.

**Conclusion:** Cybercrime often succeeds when technical weaknesses
combine with weak processes or human deception. Effective protection
requires technical controls, safe practices and timely response.

------------------------------------------------------------------------

## Q4. Compare and analyze the characteristics of low-band, mid-band, and high-band spectrum for 5G communication.

  -----------------------------------------------------------------------
  Characteristic    Low band          Mid band          High band
                                                        (mmWave)
  ----------------- ----------------- ----------------- -----------------
  Coverage          Broadest coverage Moderate coverage Shorter coverage
                    of the three                        range

  Building          Generally best    Moderate          Generally weakest
  penetration                                           

  Available         Often more        More bandwidth is Very wide
  bandwidth         limited           commonly          bandwidth can be
                                      available         available

  Potential data    Usually lower     High capacity and Very high peak
  rate              peak capacity     speed             data rates in
                                                        suitable
                                                        conditions

  Deployment        Can cover large   Moderate site     Often requires
  density           areas with fewer  density           many closely
                    sites                               spaced sites

  Best-fit use      Rural areas,      Urban/suburban    Dense venues and
                    wide-area and     general-purpose   high-capacity
                    indoor coverage   5G                hotspots
  -----------------------------------------------------------------------

### Analysis

-   **Low band** is useful when reach and reliable coverage are the main
    priorities.
-   **Mid band** is a practical balance of reach and capacity, making it
    important for broad 5G deployment.
-   **High band** can provide very high throughput but is sensitive to
    blockage and generally needs denser infrastructure.

Actual performance depends on spectrum allocation, channel bandwidth,
radio equipment, propagation conditions, and network design; a band
alone does not guarantee a particular speed.

**Diagram/reference:** [FCC --- Making Spectrum
Available](https://docs.fcc.gov/public/attachments/DOC-369307A2.pdf)

------------------------------------------------------------------------

## Q5. Compare and analyze traditional mobile network architecture with 5G architecture in terms of flexibility, scalability, and service support.

The exact details depend on which earlier-generation architecture is
used for comparison. Broadly, traditional 4G/LTE architecture is
compared with the more service-based 5G Core.

  ------------------------------------------------------------------------------
  Feature                 Traditional mobile      5G architecture
                          architecture (e.g.,     
                          4G/LTE)                 
  ----------------------- ----------------------- ------------------------------
  Core architecture       EPC with defined        5G Core with service-based
                          network functions and   architecture for many
                          interfaces              control-plane functions

  Flexibility             Virtualization is       Designed for cloud-native
                          possible, but           deployment and modular network
                          architecture is         functions
                          generally less          
                          service-oriented        

  Scalability             Can scale, but may      Network functions can be
                          require scaling         scaled and deployed more
                          particular network      flexibly
                          elements                

  Service differentiation Supports mobile         Designed to support diverse
                          broadband and QoS       service needs, including
                          mechanisms              enhanced broadband, massive
                                                  IoT and
                                                  low-latency/high-reliability
                                                  use cases

  Network slicing         Not a native end-to-end Supports network slicing to
                          capability in the same  tailor logical networks for
                          way as 5G slicing       different service requirements

  Deployment              Mature, established     Can support more flexible
                          infrastructure          cloud-based and distributed
                                                  deployments
  ------------------------------------------------------------------------------

### Analysis

5G architecture introduces a more modular, service-based core and
supports network slicing, enabling operators to tailor network resources
for different requirements. These features can improve flexibility and
service differentiation. However, actual performance and scalability
depend on implementation, capacity planning, and deployment choices; 5G
is not automatically better in every circumstance.

**Diagram/reference:** [ETSI --- 3GPP TS 23.501, 5G System Architecture
specification
(PDF)](https://www.etsi.org/deliver/etsi_TS/123500_123599/123501/18.11.00_60/ts_123501v181100p.pdf)

------------------------------------------------------------------------

## Q6. Analyze how dynamic spectrum sharing can improve the utilization of available radio spectrum.

**Dynamic Spectrum Sharing (DSS)** is a technique that allows compatible
radio technologies---commonly 4G LTE and 5G NR---to share spectrum
resources dynamically within the same frequency band, subject to the
system's design and scheduling rules.

### Working

1.  The operator has a frequency band that can support both LTE and 5G
    NR.
2.  The radio system schedules resources for the technologies according
    to traffic demand and implementation constraints.
3.  Resources can be allocated to LTE or 5G users as needed rather than
    permanently reserving the entire band for only one technology.
4.  This lets an operator introduce 5G using existing spectrum while
    continuing to support LTE devices.

### Benefits

-   Supports gradual migration from 4G to 5G.
-   Allows spectrum to be shared according to changing demand.
-   Can improve utilization when demand between technologies varies.
-   May reduce the need to dedicate separate spectrum blocks to each
    technology during transition.

### Limitations

-   Sharing has overhead and scheduling constraints.
-   Performance depends on the radio implementation and the mix of LTE
    and 5G traffic.
-   DSS does not create new spectrum; in some conditions, dedicated
    spectrum can provide better performance.

**Conclusion:** DSS can make existing spectrum more flexible and useful
during a 4G-to-5G transition, but its benefit depends on traffic
patterns and implementation.

------------------------------------------------------------------------

# Priority 3 --- Module IV: Transport Layer Protocols

*These are 2-mark questions. Keep each answer concise and focus on the
definition and main purpose.*

## Q1. Explain the purpose of transport service primitives.

Transport service primitives are operations through which an application
uses the transport layer to communicate with another application.
Typical connection-oriented primitives include **LISTEN, CONNECT,
ACCEPT, SEND, RECEIVE, and DISCONNECT**. They provide a defined
interface for establishing communication, exchanging data, and
terminating a connection.

## Q2. Explain the concept of Berkeley sockets in network communication.

Berkeley sockets are a programming interface for network communication.
A socket is an endpoint identified by addressing information and used by
a program to send or receive data. The API supports communication using
protocols such as TCP and UDP; common calls include `socket()`,
`bind()`, `connect()`, `send()` and `recv()`.

## Q3. Describe how TCP provides reliable data delivery.

TCP provides reliable, ordered delivery using sequence numbers,
acknowledgements, checksums, retransmission of lost data, and timers. It
detects missing or corrupted data and retransmits as needed, delivering
the byte stream in order to the receiving application.

## Q4. Explain the purpose of TCP flags such as SYN, ACK, FIN, and RST.

-   **SYN:** Used to initiate a connection and synchronize sequence
    numbers.
-   **ACK:** Indicates that the acknowledgement field is valid and
    acknowledges received data or connection information.
-   **FIN:** Indicates that the sender has finished sending data and
    wants to close its sending direction.
-   **RST:** Resets or aborts a TCP connection.

**Diagram/reference:** [IIT Kharagpur --- TCP notes (includes TCP
flags)](https://cse.iitkgp.ac.in/~agupta/networks/TCP.pdf)

## Q5. Explain the purpose of `socket()`, `bind()`, `listen()`, `accept()`, and `connect()` functions.

-   **`socket()`** creates a socket endpoint.
-   **`bind()`** associates a local address and port with a socket.
-   **`listen()`** marks a TCP socket as passive and ready to queue
    incoming connection requests.
-   **`accept()`** accepts a pending connection and returns a socket for
    communicating with that client.
-   **`connect()`** initiates a connection to a remote endpoint,
    commonly used by a TCP client.

## Q6. Describe how TCP provides full-duplex communication.

TCP is full-duplex because both endpoints can send and receive data
independently over the same connection at the same time. Each direction
has its own sequence and acknowledgement information, so data can flow
in both directions simultaneously.

## Q7. Explain why timers are required in TCP.

TCP uses timers to detect when expected acknowledgements do not arrive
in time and to trigger retransmission. Timers also support functions
such as connection management and persist/keepalive behaviour, helping
TCP recover from loss or avoid waiting indefinitely in certain
situations.

## Q8. Compare FTP, SFTP and SCP.

  -----------------------------------------------------------------------
  Protocol                            Purpose and key point
  ----------------------------------- -----------------------------------
  **FTP**                             Transfers files using the File
                                      Transfer Protocol; ordinary FTP
                                      does not encrypt credentials or
                                      data.

  **SFTP**                            Secure file-transfer protocol that
                                      operates over SSH and supports file
                                      operations.

  **SCP**                             Uses SSH for secure copying of
                                      files between systems;
                                      traditionally focused on copying
                                      rather than a broad file-management
                                      interface.
  -----------------------------------------------------------------------

**Remember:** SFTP is not the same protocol as FTP protected by TLS;
that latter option is called FTPS.

## Q9. Explain why real-time applications may prefer UDP.

UDP has low protocol overhead and does not require a connection setup or
retransmission of lost packets. For real-time voice, video, and gaming,
timely arrival may matter more than retransmitting late data.
Applications can implement their own reliability or loss-handling
mechanisms when needed.

------------------------------------------------------------------------

# Final Revision Checklist

## Module V --- 7 marks

-   [ ] Client-server paradigm
-   [ ] FTP vs HTTP
-   [ ] APIs for network services
-   [ ] HTTP request vs response

## Module VI --- 7 marks

-   [ ] MPLS and label forwarding
-   [ ] 5G spectrum requirements
-   [ ] Cybercrime and vulnerabilities
-   [ ] Low-, mid- and high-band spectrum
-   [ ] Traditional vs 5G architecture
-   [ ] Dynamic spectrum sharing

## Module IV --- 2 marks

-   [ ] Transport service primitives
-   [ ] Berkeley sockets
-   [ ] TCP reliability
-   [ ] TCP flags
-   [ ] Socket functions
-   [ ] Full-duplex communication
-   [ ] TCP timers
-   [ ] FTP vs SFTP vs SCP
-   [ ] UDP in real-time applications

## Study note

No explicit numerical/calculation question appears in the 19 questions
listed for this IA 2 QB. Focus first on the theory and comparison
questions above. Check lecture notes for any additional syllabus topics
not represented in the QB.
