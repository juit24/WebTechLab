# IndexedDB Components Functionality

**Human:**
Consider a web page that locally stores (using IndexDB) the details (such as name, manufacturer,
price etc) of different components(e.g. HDD, Monitor etc) of the computer. The web page contains
buttons captioned “add”, “show”, “update” and “delete”. When “add” button is clicked, the pages
shows a dialog box to get the details of the item to be added and inserts it to the IndexDB. Implement
the functionality of the other buttons. Consider (name, manufacturer) as the primary key.

***

**Assistant:**

Here's an example implementation of the described functionality using JavaScript and the IndexedDB API:

```
// Connect to the IndexedDB database
let db;
const request = window.indexedDB.open("components_db", 1);
request.onsuccess = function(event) {
  db = event.target.result;
};

// Create the object store if it doesn't exist
request.onupgradeneeded = function(event) {
  const db = event.target.result;
  const objectStore = db.createObjectStore("components", { keyPath: ["name", "manufacturer"] });
};

// Add button click event
document.getElementById("add_button").addEventListener("click", function() {
  const name = document.getElementById("name_input").value;
  const manufacturer = document.getElementById("manufacturer_input").value;
  const price = document.getElementById("price_input").value;

  const transaction = db.transaction(["components"], "readwrite");
  const objectStore = transaction.objectStore("components");
  const request = objectStore.add({ name, manufacturer, price });
  request.onsuccess = function(event) {
    console.log("Component added successfully");
  };
});

// Show button click event
document.getElementById("show_button").addEventListener("click", function() {
  const transaction = db.transaction(["components"], "readonly");
  const objectStore = transaction.objectStore("components");
  const request = objectStore.getAll();
  request.onsuccess = function(event) {
    const components = event.target.result;
    console.log(components);
  };
});

// Update button click event
document.getElementById("update_button").addEventListener("click", function() {
  const name = document.getElementById("name_input").value;
  const manufacturer = document.getElementById("manufacturer_input").value;
  const price = document.getElementById("price_input").value;

  const transaction = db.transaction(["components"], "readwrite");
  const objectStore = transaction.objectStore("components");
  const request = objectStore.get([name, manufacturer]);
  request.onsuccess = function(event) {
    const component = event.target.result;
    component.price = price;
    objectStore.put(component);
    console.log("Component updated successfully");
  };
});

// Delete button click event
document.getElementById("delete_button").addEventListener("click", function() {
  const name = document.getElementById("name_input").value;
  const manufacturer = document.getElementById("manufacturer_input").value;

  const transaction = db.transaction(["components"], "readwrite");
  const objectStore = transaction.objectStore("components");
  const request = objectStore.delete([name, manufacturer]);
  request.onsuccess = function(event) {
    console.log("Component deleted successfully");
  };
});

```

Note that this is just one possible implementation and there are different approaches that could be used.


***

**Human:**
give the html file's code

***

**Assistant:**

Here is an example HTML file that implements the buttons described in your question:

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>IndexedDB Components</title>
  </head>
  <body>
    <h1>Components</h1>
    <label for="name_input">Name:</label>
    <input type="text" id="name_input" required>
    <br><br>
    <label for="manufacturer_input">Manufacturer:</label>
    <input type="text" id="manufacturer_input" required>
    <br><br>
    <label for="price_input">Price:</label>
    <input type="number" id="price_input" required>
    <br><br>
    <button id="add_button">Add</button>
    <button id="show_button">Show</button>
    <button id="update_button">Update</button>
    <button id="delete_button">Delete</button>
    <script src="index.js"></script>
  </body>
</html>

```

This HTML file includes the input fields for the component details and the buttons described in your question. The JavaScript code that implements the functionality of the buttons is linked to the HTML file using the `script` tag.


***

Exported on 2 February 2023 9:46 pm.