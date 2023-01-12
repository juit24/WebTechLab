## 6. Write a web page home.html that loads another page (say logout.html) if user is ideal for 10 seconds.

```
<!DOCTYPE html>
<html>
<head>
  <title>Home Page</title>
</head>
<body>
  <h1>Welcome to the Home Page</h1>
  <p>You will be redirected to the logout page after 10 seconds of inactivity.</p>

  <script>
    var timeout = setTimeout(function(){
      window.location.href = 'logout.html';
    }, 10000);

    document.onmousemove = function() {
      clearTimeout(timeout);
      timeout = setTimeout(function(){
        window.location.href = 'logout.html';
      }, 10000);
    }
  </script>
</body>
</html>
```

This code creates a simple web page with a heading and a paragraph that inform the user that they will be redirected to the "logout.html" page after 10 seconds of inactivity.

The JavaScript code uses the setTimeout function to create a timer that will redirect the user to the "logout.html" page after 10 seconds. The timer is set to clear when the user moves the mouse.

When the user moves the mouse, the onmousemove event is triggered which clears the timer and sets a new timer for 10 seconds.
