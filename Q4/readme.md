## 4. Design a web page containing one text box (for login name) and one password field (for password) and a submit button. Label these items.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Login Form</title>
    </head>
    <body>
        <form action="login.php" method="post">
            <label for="username">Username:</label>
            <input type="text" id="username" name="username" required />

            <br />

            <label for="password">Password:</label>
            <input type="password" id="password" name="password" required />

            <br /><br />

            <input type="submit" value="Submit" />
        </form>
    </body>
</html>
```

This code creates a simple login form with a text box for login name, a password field for password, and a submit button.

-   The label element is used to label each field and the for attribute is used to associate the label with the corresponding input field.

-   The input elements are used to create the text box and password field, respectively. The type attribute is used to specify the type of input field, and the name attribute is used to give the input field a name that can be used to identify it on the server-side.
-   The attribute required is used to make sure the fields are filled before the form is submitted.
-   The form element is used to create the form, and the action attribute is set to "login.php" to specify the server-side script that will handle the form submission. The method attribute is set to "post" to indicate that the form data should be sent as a HTTP POST request.
-   The input element with type="submit" and value="Submit" is used to create the submit button.

### This is a basic example, in a real-world scenario you should handle the server-side validation and security measures, like encrypting the password, validating the form inputs, and so on.
