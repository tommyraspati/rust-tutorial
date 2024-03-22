# Commit 1 Reflection notes
## Handle Connection Function in Rust

The handle_connection function in this Rust program is responsible for handling each incoming TCP connection. It reads the incoming data from the client line by line and processes the HTTP request.
How handle_connection Works

- Accepts a TcpStream: The handle_connection function takes a TcpStream as an argument, representing the connection to the client.

- Creates a BufReader: It creates a BufReader from the TcpStream to efficiently read lines of text.

- Reads HTTP Request: It reads the HTTP request line by line using the lines() method provided by BufReader. Each line is stored in a Vec<String> called http_request.

- Collects Request Lines: The take_while() method is used to collect lines until an empty line is encountered, indicating the end of the request headers.

- Prints Request: Finally, the function prints the collected HTTP request headers using println!().

# Commit 2 Reflection notes

## Returning HTML
In the second commit, the handle_connection function was updated to return an HTML response. Here's the updated implementation:

- Reads the HTTP request headers as before.
- Prepares an HTTP response with a status line, content length, and contents of an hello.html file.
- Sends the HTML response back to the client.

Here is the output of the html if we run it on local
![Commit 2 screen capture](/assets/images/commit2.png)

# Commit 3 Reflection notes

## Validating request and selectively responding

In the third commit, the handle_connection function was further updated to validate the incoming HTTP request and selectively respond based on the requested URL:

- Validates Request: The function now checks the request line to determine whether the client is requesting the hello.html page or an undefined route.
- Selectively Responds: Based on the validation, the function responds with either:
    - The contents of hello.html and a 200 OK status if the request is valid.
    - The contents of error.html and a 404 NOT FOUND status if the request is for an undefined route.
- Error Handling: An error.html file was created to display a custom error message when the requested page is not available.

Example of url other than http://127.0.0.1:7878/:
![Commit 3 screen capture](/assets/images/commit3_bad.png)

# Commit 4 Reflection notes

## Simulation slow response

In the fourth commit, the handle_connection function was updated to simulate a slow response for a specific route. This addition is meant to demonstrate how the server behaves when a request takes longer to process.

### Implementation Details:

- New Route /sleep: A new route GET /sleep HTTP/1.1 was introduced. When this route is accessed, the server simulates a slow response by pausing for 10 seconds before sending the response.

- Thread Sleep: The thread::sleep(Duration::from_secs(10)); function is used to create the delay. This function puts the current thread to sleep for the specified duration, effectively blocking the server from processing other requests during this time.

### Observations:

- Blocking Behavior: When the /sleep route is accessed, the server becomes unresponsive to other requests until the sleep duration is over. This is because the server is running in a single-threaded, blocking mode, and cannot handle multiple requests simultaneously.

- Impact on User Experience: This simulation demonstrates how a long-running operation on the server can impact the user experience by causing delays in response times. In a real-world scenario, it's important to handle such operations asynchronously or in a separate thread to avoid blocking the server.
