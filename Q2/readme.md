## 2. Using telnet application and HTTP, obtain the file first.html from a remote machine.

To obtain the file "first.html" from a remote machine using telnet and HTTP, you would first need to have telnet installed on your local machine. You can then open a command prompt or terminal and use the telnet command to connect to the remote machine.

Assuming the IP address of the remote machine is "192.168.1.100" and the web server on that machine is running on port 80, you would enter the following command to connect:

```
telnet 192.168.1.100 80
```

Once connected, you can send an HTTP GET request to retrieve the file "first.html" by typing in the following command:

```
GET /first.html HTTP/1.1
```

And then hit enter twice.

You should then receive a response from the server, which will include the contents of the "first.html" file if it exists and is accessible. The response will also include information such as the HTTP status code and any headers.

Please note that this method is less common, typically developers use a browser or http client library to retrieve the files from remote servers. Additionally, telnet is not a secure protocol and it is recommended to use ssh or https for this kind of operations.
