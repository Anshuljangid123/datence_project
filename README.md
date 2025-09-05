A full-stack web application that fetches book data from an external source, stores it in a MongoDB database, and displays it on a modern React frontend. Users can browse, search, filter, and view book details.

Project Structure

root/
 ├─ backend/      # Express.js backend, MongoDB, scraping logic
 ├─ frontend/     # React + Vite frontend
 └─ scraper/      # Web scraping scripts


1. Backend Setup

a . Navigate to the backend folder:
    cd backend
    
b . Install dependencies:
    npm install


c. Create a .env file with your MongoDB URL:

  MONGODB_URL=mongodb+srv://<username>:<password>@cluster.mongodb.net/books
  PORT=3000

d. Start the backend in development mode:
  npm run dev


the server runs at http://localhost:3000


API routes:
GET /api/books → fetch books (supports query params for pagination, search, filters)
GET /api/books/:id → fetch book details

POST /api/books/refresh → trigger scraping and refresh database


2. Scraper

The scraper fetches book data from the source website and stores it in MongoDB. It is automatically integrated with the backend.

To manually run the scraper:

cd scraper
node scraper.js

Or trigger via backend API:
POST http://localhost:3000/api/books/refresh

3. Frontend Setup

Navigate to the frontend folder:
cd frontend


Install dependencies:
npm install


Configure backend API URL:
In src/services/bookService.js, set BASE_URL to your backend:

const BASE_URL = "http://localhost:3000/api/books"; // local dev

Start the frontend in development mode:
npm run dev


The app runs at http://localhost:5173 (Vite default)

Build for production:
npm run build

4. Deployment

Deploy backend on Vercel using src/server.js as the entry point.
Deploy frontend on Vercel using the dist folder as output.

5. Features

Browse books with pagination
Search by title
Filter by rating, price, availability
View book details
Refresh database by scraping new data


