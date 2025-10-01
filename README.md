
!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Contact Form</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f7f7f7;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    form {
      background: #fff;
      padding: 20px 25px;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      width: 320px;
    }
    h2 {
      text-align: center;
      margin-bottom: 15px;
      color: #333;
    }
    label {
      font-size: 14px;
      font-weight: bold;
      margin-top: 10px;
      display: block;
    }
    input, textarea, button {
      width: 100%;
      padding: 10px;
      margin: 6px 0;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 14px;
    }
    button {
      background: #007bff;
      color: white;
      font-size: 15px;
      border: none;
      cursor: pointer;
      margin-top: 10px;
    }
    button:hover {
      background: #0056b3;
    }
    .error {
      color: red;
      font-size: 13px;
      margin-bottom: 5px;
      display: block;
    }
  </style>
</head>
<body>
  <form id="contactForm">
    <h2>Contact Us</h2>

    <label for="name">Name</label>
    <input type="text" id="name" placeholder="Enter your name">
    <span id="nameError" class="error"></span>

    <label for="email">Email</label>
    <input type="text" id="email" placeholder="Enter your email">
    <span id="emailError" class="error"></span>

    <label for="phone">Phone</label>
    <input type="text" id="phone" placeholder="Enter phone number">
    <span id="phoneError" class="error"></span>

    <label for="message">Message</label>
    <textarea id="message" placeholder="Write your message"></textarea>
    <span id="messageError" class="error"></span>

    <button type="submit">Send Message</button>
  </form>

  <script>
    const form = document.getElementById("contactForm");

    form.addEventListener("submit", function(event) {
      event.preventDefault(); // stop form from submitting
      let valid = true;

      // Name validation
      const name = document.getElementById("name").value.trim();
      const nameError = document.getElementById("nameError");
      if (name === "") {
        nameError.textContent = "Name is required.";
        valid = false;
      } else {
        nameError.textContent = "";
      }

      // Email validation
      const email = document.getElementById("email").value.trim();
      const emailError = document.getElementById("emailError");
      const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
      if (email === "") {
        emailError.textContent = "Email is required.";
        valid = false;
      } else if (!email.match(emailPattern)) {
        emailError.textContent = "Enter a valid email address.";
        valid = false;
      } else {
        emailError.textContent = "";
      }

      // Phone validation (digits only, 10 digits)
      const phone = document.getElementById("phone").value.trim();
      const phoneError = document.getElementById("phoneError");
      const phonePattern = /^[0-9]{10}$/;
      if (phone === "") {
        phoneError.textContent = "Phone number is required.";
        valid = false;
      } else if (!phone.match(phonePattern)) {
        phoneError.textContent = "Enter a valid 10-digit phone number.";
        valid = false;
      } else {
        phoneError.textContent = "";
      }

      // Message validation
      const message = document.getElementById("message").value.trim();
      const messageError = document.getElementById("messageError");
      if (message === "") {
        messageError.textContent = "Message cannot be empty.";
        valid = false;
      } else {
        messageError.textContent = "";
      }

      if (valid) {
        alert("Form submitted successfully ✅");
        form.reset();
      }
    });
  </script>
</body>
</html>
