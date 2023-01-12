## 5. Write a necessary JavaScript functions to verify the content of text box and password field in previous assignments. If there is any error, show appropriate message in red color in a label. Use following rules: A login name can only have alphanumeric characters and „\_‟(underscore)Number of characters in the login must not exceed 10 A password must have 6 to 10 characters containing at least one digit and one uppercase letter.

Here is an example of a JavaScript function that can be used to verify the content of the text box and password field in the previous HTML form:

```
function validateForm() {
    var username = document.getElementById("username").value;
    var password = document.getElementById("password").value;
    var errorLabel = document.getElementById("errorLabel");
    var isValid = true;

    // Validate the login name
    if (!/^[a-zA-Z0-9_]+$/.test(username) || username.length > 10) {
        errorLabel.innerHTML = "Error: Login name can only have alphanumeric characters and '_' and must not exceed 10 characters.";
        errorLabel.style.color = "red";
        isValid = false;
    }

    // Validate the password
    if (!/^(?=.*[0-9])(?=.*[A-Z])[a-zA-Z0-9]{6,10}$/.test(password)) {
        errorLabel.innerHTML = "Error: Password must have 6 to 10 characters containing at least one digit and one uppercase letter.";
        errorLabel.style.color = "red";
        isValid = false;
    }

    if (isValid) {
        errorLabel.innerHTML = "";
        // form can be submitted
    }
    return isValid;
}
```

This function first gets the value of the "username" and "password" fields by using document.getElementById("username").value; and document.getElementById("password").value; respectively.
Then it gets the error label element by using document.getElementById("errorLabel").
It then uses regular expressions to check if the login name only contains alphanumeric characters and "\_" and doesn't exceed 10 characters. It also checks if the password contains 6-10 characters, with at least one digit and one uppercase letter. If the validation fails, it shows an error message in red color using the errorLabel element and sets the isValid variable to false. If the validation passes, the errorLabel element is emptied and the form can be submitted.

Note that this is a simple example, in a real-world scenario you should handle different edge cases and also use libraries to validate the form inputs.

You should also add the following code to your HTML form to call the validateForm() function when the form is submitted:

```
<form action="login.php" method="post" onsubmit="return validateForm()">
```

It's important to note that this function can only prevent the user from submitting the form with invalid data. But it doesn't protect against malicious inputs being sent to the server. To secure the form, you should use server-side validation and also consider other security measures such as encryption and sanitization of the inputs.
