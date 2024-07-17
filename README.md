# Online-Quiz-System
Online Quiz System (using TCP Multithreading to cater unlimited clients at the same time) 

### Overview:
The Online Quiz System is designed to provide a scalable and efficient solution for conducting online tests across multiple subjects using TCP multithreading. The system consists of a main server, three sub-servers (each dedicated to a specific subject: Science, Mathematics, and English), and multiple clients. The main server handles client requests by directing them to the appropriate sub-server, which conducts the tests and returns the results. This architecture ensures that the main server is not overburdened by direct communication with clients, enhancing overall system performance and scalability.

### Test Categories and Subcategories:
1. **Science**
   - Physics
   - Chemistry
   - Biology

2. **Mathematics**
   - Geometry
   - Algebra
   - IQ

3. **English**
   - Analogies
   - Antonyms
   - Reading Comprehension (RC) Questions

### System Components and Workflow:

#### 1. Main Server
- **Functionality:** 
  - Receives connections from clients and directs them to the appropriate sub-server based on the test type requested.
  - Maintains a database of sub-server information (test type, IP address, and port number).
  - Stores client test results received from sub-servers in a file.
- **Communication Protocol:**
  - Receives sub-server details in the format: `Test_name, Sub-server IP, Sub-server Port`
  - Sends sub-server information to clients in the format: `Test_name, Sub-server IP, Sub-server Port`
  - Receives client results in the format: `Client IP, Client Port, Test Name, Test Type, Marks`

#### 2. Sub-Servers (Science, Mathematics, English)
- **Functionality:**
  - Connect to the main server and provide their details.
  - Handle client connections, present available test types, assign random marks, and send results back to the main server and clients.
- **Communication Protocol:**
  - Send initial connection details to the main server in the format: `Test_name, Sub-server IP, Sub-server Port`
  - Receive client requests for specific test types and assign random marks.
  - Send results back to the main server and clients in the format: `Client IP, Client Port, Test Name, Test Type, Marks`

#### 3. Client
- **Functionality:**
  - Connect to the main server and request a specific test type.
  - Receive sub-server details from the main server and establish a connection with the relevant sub-server.
  - Select a test type from the options provided by the sub-server, complete the test, and receive marks.
  - Display test results and terminate the connection.
- **Communication Protocol:**
  - Receive sub-server information from the main server in the format: `Test_name, Sub-server IP, Sub-server Port`
  - Receive test results from the sub-server in the format: `Client IP, Client Port, Test Name, Test Type, Marks`

### Implementation Details:

#### Main Server:
1. **Initialize the main server:** Set up TCP connection to listen for sub-server and client connections.
2. **Handle sub-server registration:** Receive and store sub-server details.
3. **Handle client requests:** Display test options, receive client choice, retrieve corresponding sub-server details, and send them to the client.
4. **Store client results:** Receive and log test results in a file.

#### Sub-Servers:
1. **Initialize the sub-server:** Set up TCP connection and register with the main server.
2. **Handle client connections:** Present test type options, assign random marks, and send results to the main server and clients.
3. **Random marks assignment:** Use a random number generator to assign marks between 1 and 100.

#### Client:
1. **Connect to the main server:** Request a specific test type.
2. **Receive sub-server details:** Establish connection with the appropriate sub-server.
3. **Select and complete the test:** Choose a test type and receive marks.
4. **Display results:** Show the results on the terminal and terminate the connection.

### Conclusion:
The Online Quiz System project demonstrates the use of TCP multithreading to manage multiple clients efficiently while distributing the workload across multiple sub-servers. By implementing this system, the project showcases skills in network programming, server-client communication, and multithreading. The architecture ensures scalability, responsiveness, and effective resource management, making it suitable for large-scale deployment in educational environments.



