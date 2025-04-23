# COMPANY-WEBSITE
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Business Dashboard</title>
  <link rel="stylesheet" href="styles.css">
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #f4f4f4;
      color: #333;
    }
    header {
      background: #003366;
      color: white;
      padding: 1rem 2rem;
    }
    nav ul {
      list-style: none;
      display: flex;
      gap: 1rem;
      padding: 0;
    }
    nav ul li a {
      color: white;
      text-decoration: none;
    }
    section {
      padding: 2rem;
      background: white;
      margin: 1rem 2rem;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    form label {
      display: block;
      margin: 0.5rem 0 0.2rem;
    }
    input, button {
      padding: 0.5rem;
      margin-bottom: 1rem;
      width: 100%;
      max-width: 400px;
      display: block;
    }
    button {
      background: #003366;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background: #0055a5;
    }
    #invoiceList, #driverList, #salaryList {
      margin-top: 1rem;
    }
  </style>
</head>
<body>
  <header>
    <h1>Business Dashboard</h1>
    <nav>
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#invoices">Invoices</a></li>
        <li><a href="#drivers">Driver Details</a></li>
        <li><a href="#salary">Salary Platform</a></li>
      </ul>
    </nav>
  </header>  <section id="home">
    <h2>Welcome to the Business Dashboard</h2>
    <p>Manage your operations efficiently from one platform.</p>
  </section>  <section id="invoices">
    <h2>Invoices</h2>
    <form>
      <label for="invoiceUpload">Upload Invoice:</label>
      <input type="file" id="invoiceUpload" name="invoiceUpload">
      <button type="submit">Submit</button>
    </form>
    <div id="invoiceList"></div>
  </section>  <section id="drivers">
    <h2>Driver Details</h2>
    <form id="driverForm">
      <label>Name: <input type="text" name="name"></label>
      <label>Contact: <input type="text" name="contact"></label>
      <label>License Number: <input type="text" name="license"></label>
      <button type="submit">Add Driver</button>
    </form>
    <div id="driverList"></div>
  </section>  <section id="salary">
    <h2>Salary Platform</h2>
    <form id="salaryForm">
      <label>Driver Name: <input type="text" name="driverName"></label>
      <label>Amount: <input type="number" name="amount"></label>
      <button type="submit">Submit Salary</button>
    </form>
    <div id="salaryList"></div>
  </section>  <script>
    document.getElementById('driverForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const name = this.name.value;
      const contact = this.contact.value;
      const license = this.license.value;
      const entry = `<p><strong>${name}</strong> | ${contact} | License: ${license}</p>`;
      document.getElementById('driverList').innerHTML += entry;
      this.reset();
    });

    document.getElementById('salaryForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const driverName = this.driverName.value;
      const amount = this.amount.value;
      const entry = `<p><strong>${driverName}</strong> - $${amount}</p>`;
      document.getElementById('salaryList').innerHTML += entry;
      this.reset();
    });

    document.querySelector('#invoices form').addEventListener('submit', function(e) {
      e.preventDefault();
      const fileInput = document.getElementById('invoiceUpload');
      if (fileInput.files.length > 0) {
        const fileName = fileInput.files[0].name;
        const entry = `<p>Uploaded: ${fileName}</p>`;
        document.getElementById('invoiceList').innerHTML += entry;
        fileInput.value = '';
      }
    });
  </script></body>
</html>
