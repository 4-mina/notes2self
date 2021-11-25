# Sockets
Sockets are basically a combination of an IP address and a port representing one endpoint in a two-way communication over the network ( using TCP). 
**On the client side:** The client knows the hostname of the machine the server is running on and the port on which it is listening. 
**On the server side:** The server has an assigned port on which it listens for client connection. Once a client connects to the server, the later create a new socket for communication with the client and keeps on listening for other connections on the server socket.
# Steps in code (java)

## Server Side

- **Creating the server socket:** 
`Server Socket serverSocket= new ServerSocket("IP @", port); // IP address to be replaced by localhost in case the server is running locally, or the IP address otherwise. The port is to be replace by a port number > 1024 ( since ports under 1024 are reserved).`

- **Creating a new socket object upon client connection:**
Here the _accept()_ method is triggered once a client connects to the server and returns a socket object which is then used by the server to communicate with this specific client.
`Socket socket= serverSocket.accept();`

- **Creating DataInputStream and DataOutputStream objects:**
These are respectively used to read incoming data stream from the client and write to the client side, using the previously created socket.
`DataInputStream dataInputStream= new DataInputStream(socket.getInputStream());`
`DataOutputStream dataOutputStream= new DataOutputStream(socket.getOutputStream());`

- **Reading Strings**
+ Using _readUTF()_:
This method of DataInputStream class allows the server to read an input stream sent through an output stream on the client side.
`String received = dataInputStream.readUTF(); //reading received stream from the client`
`System.out.println(received);`
**PS:** _DataInputStream_ is however not safe for multithreaded access. Hence, the best way would be to use _BufferedReader_ and _InputStreamReader_.

+ Using _Bufferedreader_ and _InputStreamReader_:
We first use InputStreamReader which reads one character(4 bytes):
`InputStreamReader inputStreamReader= new InputStreamReader(dataInputStream);`
However, as we wish to read a whole string and not just one character, we use BufferedReader:
`BufferedReader bufferedReader= new BufferedReader(inputStreamReader);`
`String received= bufferedReader.readLine();`

- **Writing Strings**

+ Using _writeUTF()_:
This method of DataOutputStream class uses data output stream to allow the server to write data that can be read later, on the client side, using a data input stream.
` dataOutputStream.writeUTF("Hello from the server side");`

+ Using _PrintWriter_: 
To write data on the client side we use _PrintWriter_ on the output stream, the methos also take a flag which decides if the received stream is automatically sent to the client.This flag is set to false by default.
`PrintWriter printWriter= new PrintWriter(dataOutputStream,true);`  
`printWriter.println(" Hello from the server side");` 

- **Reading Objects**
In this case we simply replace the _InputStreamReader_ used to read strings with _ObjectInputStream_
`IntputObjectStream inputObjectStream= new InputObjectStream(dataInputStream);`
`ObjectClassName object= (ObjectClassName) inputObjectStream.readObject();`
- **Writing Objects**
`OutputObjectStream ouputObjectStream= new OuputObjectStream(dataOutputStream);`
`outputObjectStream.write(object);`
## Client Side