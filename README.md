# 🧮 Factorial Backend API

A lightweight and scalable backend server built with **Node.js**, **Express**, and **MySQL (optional)**. This API calculates the factorial of a number provided via a POST request. Designed as a simple learning project for beginners in RESTful APIs.

---

## 🚀 Features

- ✅ Calculates factorial for non-negative integers
- 🧾 Input validation and error handling
- 🔄 Auto-restarts with `nodemon` for easy development
- 🔓 CORS-enabled for frontend communication
- 🛢️ MySQL-ready (though not required for factorial logic)

---

## 🛠️ Tech Stack

- [Node.js](https://nodejs.org/)
- [Express.js](https://expressjs.com/)
- [CORS](https://www.npmjs.com/package/cors)
- [MySQL2](https://www.npmjs.com/package/mysql2)
- [Nodemon](https://www.npmjs.com/package/nodemon)

---

## 📦 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/aaditya09750/Factorial.git
cd Factorial
```

### 2. Install Dependencies

```bash
npm install express cors mysql2
npm install -g nodemon
```

### 3. Run the Server

```bash
nodemon index.js
```

> The server will start on: `http://localhost:3000`

---

## 📡 API Reference

### POST `/factorial`

**Request:**

```json
{
  "number": 5
}
```

**Response:**

```json
{
  "result": 120
}
```

### Input Validation:

- Accepts only **non-negative integers**
- Returns error if input is invalid or missing

---

## 🔁 Sample Request with `curl`

```bash
curl -X POST http://localhost:3000/factorial \
  -H "Content-Type: application/json" \
  -d '{"number": 6}'
```

**Response:**
```json
{
  "result": 720
}
```

---

## 📄 Source Code (`index.js`)

```js
const express = require("express");
const cors = require("cors");

const app = express();
app.use(cors());
app.use(express.json());

app.post("/factorial", (req, res) => {
  const num = req.body.number;

  if (typeof num !== "number" || num < 0 || !Number.isInteger(num)) {
    return res.status(400).json({
      error: "Invalid input. Please provide a non-negative integer.",
    });
  }

  let result = 1;
  for (let i = 2; i <= num; i++) {
    result *= i;
  }

  res.json({ result });
});

app.listen(3000, () => {
  console.log("✅ Server is running on http://localhost:3000");
});
```

---

## 👨‍💻 Author

**Aaditya Gunjal**  
🔗 [GitHub Profile](https://github.com/aaditya09750)

---

