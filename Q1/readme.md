## 1. Download apache tomcat (.zip) and install(unzip) it. Read documentation and configure tomcat. Check the port it uses. Start the web server. Check if it is working or not. Now, write a simple HTML file (say first.html) containing your name and put it in the web server‟s ROOT directory. Now check if it is available through the web browser and appropriate URL. Change the port of the web server to 8002 and restart the web server. Check if it is working or not.

To download Apache Tomcat, go to the official website (https://tomcat.apache.org/) and select the latest version in the form of a .zip file. Once the download is complete, unzip the file to a directory of your choice.

To install and configure Tomcat, read the documentation provided in the "docs" directory within the unzipped Tomcat folder. This documentation should provide instructions on how to configure the server and set the desired port. By default, Tomcat uses port 8080, but you can change this to 8002 as you have mentioned in your question.

To start the web server, navigate to the "bin" directory within the Tomcat folder and start the server using the appropriate command for your operating system. For example, on Windows, you would use the command "startup.bat" and on Linux, the command "./catalina.sh run".

To check if the web server is working, open a web browser and navigate to "http://localhost:8080" (or "http://localhost:8002" if you have changed the port as mentioned in your question). If the server is running, you should see the default Tomcat page.

To create a simple HTML file containing your name, use a text editor to create a new file called "first.html" and add the following code:

```
<html>
<head>
  <title>My Name</title>
</head>
<body>
  <h1>My name is [YOUR NAME]</h1>
</body>
</html>
```

Then save the file in the "webapps/ROOT" directory within the Tomcat folder.

To check if the file is available through a web browser, navigate to "http://localhost:8080/first.html" (or "http://localhost:8002/first.html" if you have changed the port as mentioned in your question). If the server is running and the file is in the correct location, you should see the page with your name.

Finally, to change the port of the web server to 8002 and restart the web server, you need to edit the server.xml file in the conf directory, look for the connector on port 8080, change it to 8002 and then restart the server.
