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
