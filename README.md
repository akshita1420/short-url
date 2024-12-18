# Short URL Service

**Note: Remember I made this project for my learning purpose only hence it will show local host**

This project is a **URL Shortener** application built using **Node.js**, **Express.js**, and **MongoDB**. It allows users to generate short URLs for long URLs and tracks analytics such as the number of times a short URL was visited.

## 🚀 **Features**
- **Shorten URLs**: Convert long URLs into short, shareable links.
- **Redirect URLs**: Access the original URL by visiting the short URL.
- **Click Analytics**: Track how many times a short URL was visited.

---

## 🛠️ **Tech Stack**
- **Node.js**: JavaScript runtime for server-side development.
- **Express.js**: Web framework for building the API.
- **MongoDB**: NoSQL database to store URLs and visit history.

---

## 📁 **Project Structure**
```
short-url/
├── controllers/
│   └── url.js            # Handles the business logic for URL generation & analytics
├── models/
│   └── url.js            # Mongoose schema for URL documents
├── routes/
│   └── url.js            # Routes for URL endpoints
├── index.js              # Main entry point of the server
└── README.md             # Project documentation (this file)
```

---

## ⚙️ **Installation**
1. Clone the repository:
   ```bash
   git clone https://github.com/akshita1420/short-url.git
   cd short-url
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the MongoDB server locally (or use a cloud service like MongoDB Atlas):
   ```bash
   mongod
   ```

4. Start the Node.js server:
   ```bash
   node index.js
   ```

The server will start on **http://localhost:8001**. (Remember I made this project for my learning purpose only)

---

## 🔥 **Usage**

### 1️⃣ **Shorten a URL**
**Endpoint**: `POST /url`

**Request Body**:
```json
{
  "url": "https://example.com"
}
```

**Response**:
```json
{
  "id": "sbhPGQHx"
}
```
This generates a new short URL with ID **sbhPGQHx**.

---

### 2️⃣ **Access a Shortened URL**
**Endpoint**: `GET /:shortId`

When you visit **http://localhost:8001/sbhPGQHx**, you will be redirected to **https://example.com**.

---

### 3️⃣ **View Analytics**
**Endpoint**: `GET /url/analytics/:shortId`

**Response**:
```json
{
  "totalClicks": 5,
  "analytics": [
    { "timestamp": 1697364012345 },
    { "timestamp": 1697365012345 },
    { "timestamp": 1697366012345 }
  ]
}
```
This endpoint shows how many times the short URL has been visited, along with the visit timestamps.

---

## 📚 **API Endpoints**
| **Method** | **Endpoint**           | **Description**         |
|------------|-----------------------|-------------------------|
| `POST`     | `/url`                 | Create a short URL      |
| `GET`      | `/:shortId`           | Redirect to long URL    |
| `GET`      | `/url/analytics/:shortId` | View analytics for short URL |

---

## 📘 **Examples**
### 1️⃣ **Create a short URL**
```bash
curl -X POST http://localhost:8001/url \
     -H 'Content-Type: application/json' \
     -d '{ "url": "https://piyushgarg.dev" }'
```

### 2️⃣ **Access the short URL**
```bash
curl http://localhost:8001/sbhPGQHx
```
This will redirect you to **https://piyushgarg.dev**.

### 3️⃣ **View URL analytics**
```bash
curl http://localhost:8001/url/analytics/sbhPGQHx
```

---

## 🐛 **Common Issues**
- **MongoDB Connection Failed**: Make sure MongoDB is running locally or that you have provided the correct connection string.
- **Port Already in Use**: The default port is **8001**, so ensure that no other service is using it.

---

## ✨ **Future Enhancements**
- **Custom Short URLs**: Allow users to define custom short URLs.
- **User Authentication**: Add user accounts to track personal URL analytics.
- **Enhanced Analytics**: Show more analytics like geolocation, device, and browser info.

---

## 🧑‍💻 **Author**
Created by **Akshita Sahu**. Feel free to reach out for feedback or collaboration!

---

## 📝 **License**
This project is licensed under the MIT License.

