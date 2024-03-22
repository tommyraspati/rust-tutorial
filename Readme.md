# Commit 1 Reflection notes
## Handle Connection Function in Rust

The handle_connection function in this Rust program is responsible for handling each incoming TCP connection. It reads the incoming data from the client line by line and processes the HTTP request.
How handle_connection Works

- Accepts a TcpStream: The handle_connection function takes a TcpStream as an argument, representing the connection to the client.

- Creates a BufReader: It creates a BufReader from the TcpStream to efficiently read lines of text.

- Reads HTTP Request: It reads the HTTP request line by line using the lines() method provided by BufReader. Each line is stored in a Vec<String> called http_request.

- Collects Request Lines: The take_while() method is used to collect lines until an empty line is encountered, indicating the end of the request headers.

- Prints Request: Finally, the function prints the collected HTTP request headers using println!().