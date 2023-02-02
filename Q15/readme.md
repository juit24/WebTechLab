# New chat

**Human:**
Write a web page that generates a factorial table using a web worker. The main page sends an integer
number (say 5) and the worker returns the factorial table (1 to 5) and the main page finally displays it.

***

**Assistant:**

Here's a simple HTML, JavaScript and CSS code to achieve the requirement:

```
<!DOCTYPE html>
<html>
  <head>
    <style>
      table {
        font-family: arial, sans-serif;
        border-collapse: collapse;
        width: 100%;
      }

      td, th {
        border: 1px solid #dddddd;
        text-align: left;
        padding: 8px;
      }

      tr:nth-child(even) {
        background-color: #dddddd;
      }
    </style>
  </head>
  <body>
    <h2>Factorial Table</h2>
    <input type="number" id="inputNumber" value="5">
    <button id="generateButton">Generate</button>
    <br><br>
    <table id="factorialTable">
      <thead>
        <tr>
          <th>Number</th>
          <th>Factorial</th>
        </tr>
      </thead>
      <tbody id="factorialBody">
      </tbody>
    </table>

    <script>
      const generateButton = document.getElementById("generateButton");
      const inputNumber = document.getElementById("inputNumber");
      const factorialBody = document.getElementById("factorialBody");

      generateButton.addEventListener("click", () => {
        const worker = new Worker("factorial-worker.js");
        worker.postMessage(inputNumber.value);

        worker.onmessage = function (e) {
          factorialBody.innerHTML = "";
          e.data.forEach(element => {
            factorialBody.innerHTML += `
            <tr>
              <td>${element.number}</td>
              <td>${element.factorial}</td>
            </tr>
            `;
          });
        };
      });
    </script>
  </body>
</html>

```

And here's the code for the web worker `factorial-worker.js`:

```
onmessage = function (e) {
  const n = e.data;
  let result = [];

  for (let i = 1; i <= n; i++) {
    let factorial = 1;
    for (let j = 1; j <= i; j++) {
      factorial *= j;
    }
    result.push({ number: i, factorial: factorial });
  }

  postMessage(result);
};

```

You can save the HTML file and the web worker JavaScript file in the same directory and run the HTML file in the browser. Enter a number in the input field and click on the "Generate" button to get the factorial table.


***

**Human:**
is it the correct code inside the factorial-worker.js?

***

**Assistant:**

Yes, the code inside `factorial-worker.js` is correct. When the main page sends a message to the worker with a number, the worker calculates the factorials of numbers from 1 to that number and returns the result as an array of objects, each containing a number and its corresponding factorial. The main page receives this result, loops through it and generates the table rows, finally displaying the factorial table.


***

Exported on 2 February 2023 9:51 pm.