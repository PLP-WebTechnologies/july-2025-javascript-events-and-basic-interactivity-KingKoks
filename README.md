project/
│── index.html
│── style.css
│── script.js


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive Web Page</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Interactive Web Page</h1>

  <!-- Interactive Section 1: Form -->
  <section>
    <h2>Sign Up Form</h2>
    <form id="signupForm">
      <label for="username">Username:</label>
      <input type="text" id="username" placeholder="Enter username"><br><br>

      <label for="email">Email:</label>
      <input type="text" id="email" placeholder="Enter email"><br><br>

      <label for="password">Password:</label>
      <input type="password" id="password" placeholder="Enter password"><br><br>

      <button type="submit">Submit</button>
    </form>
    <p id="formMessage"></p>
  </section>

  <!-- Interactive Section 2: Button-triggered greeting -->
  <section>
    <h2>Greeting Section</h2>
    <button id="greetBtn">Say Hello</button>
    <p id="greetOutput"></p>
  </section>

  <!-- Interactive Section 3: Color changer -->
  <section>
    <h2>Background Color Changer</h2>
    <button id="colorBtn">Change Background</button>
  </section>

  <script src="script.js"></script>
</body>
</html>


body {
  font-family: Arial, sans-serif;
  margin: 30px;
  background-color: #f9f9f9;
  color: #333;
}

h1, h2 {
  color: #2c3e50;
}

form {
  margin: 15px 0;
  padding: 15px;
  background: #eef;
  border-radius: 8px;
  width: 300px;
}

input {
  width: 90%;
  padding: 8px;
  margin: 5px 0;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  margin-top: 10px;
  padding: 8px 15px;
  background: #4CAF50;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background: #45a049;
}

#formMessage {
  margin-top: 10px;
  font-weight: bold;
}


// =============================
// Event Handling + Interactive Features
// =============================

// Feature 1: Greeting button
document.getElementById("greetBtn").addEventListener("click", function() {
  document.getElementById("greetOutput").innerText = "Hello there! 👋 Welcome to the site.";
});

// Feature 2: Background color changer
document.getElementById("colorBtn").addEventListener("click", function() {
  let colors = ["lightblue", "lightgreen", "lightyellow", "lavender", "#f9f9f9"];
  let currentColor = document.body.style.backgroundColor;
  let newColor = colors[Math.floor(Math.random() * colors.length)];
  while (newColor === currentColor) {
    newColor = colors[Math.floor(Math.random() * colors.length)];
  }
  document.body.style.backgroundColor = newColor;
});

// =============================
// Custom Form Validation
// =============================
document.getElementById("signupForm").addEventListener("submit", function(e) {
  e.preventDefault(); // Stop form submission

  let username = document.getElementById("username").value.trim();
  let email = document.getElementById("email").value.trim();
  let password = document.getElementById("password").value.trim();
  let message = "";

  // Username validation
  if (username.length < 3) {
    message = "❌ Username must be at least 3 characters.";
  }
  // Email validation (basic regex)
  else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
    message = "❌ Please enter a valid email address.";
  }
  // Password validation
  else if (password.length < 6) {
    message = "❌ Password must be at least 6 characters.";
  } 
  else {
    message = "✅ Form submitted successfully! Welcome, " + username + "!";
  }

  document.getElementById("formMessage").innerText = message;
});
