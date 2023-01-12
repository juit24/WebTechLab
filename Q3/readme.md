## Now, write Java socket program to obtain the file first.html from a remote machine.(optional assignment)

This program is used to obtain the file "first.html" from a remote machine using Java sockets.

```java
import java.io.*;
import java.net.*;

public class FileDownloader {
    public static void main(String[] args) {
        String host = "192.168.1.100";
        int port = 80;
        String fileToDownload = "/first.html";

        try (Socket socket = new Socket(host, port)) {
            OutputStream out = socket.getOutputStream();
            PrintWriter writer = new PrintWriter(out);

            // Send an HTTP GET request to the server to retrieve the file
            writer.println("GET " + fileToDownload + " HTTP/1.1");
            writer.println("Host: " + host);
            writer.println();
            writer.flush();

            // Read the response from the server
            InputStream in = socket.getInputStream();
            BufferedReader reader = new BufferedReader(new InputStreamReader(in));

            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }

            writer.close();
            reader.close();
        } catch (UnknownHostException e) {
            System.err.println("Cannot find host: " + host);
        } catch (IOException e) {
            System.err.println("I/O error: " + e);
        }
    }
}
```
