# Civic Ballot — React frontend

Your original Express backend (server.js + JSON files) is unchanged.
Only the frontend is rebuilt in React (Vite).

## Folder layout (put `client/` next to your existing server.js)

    your-project/
    ├── server.js
    ├── package.json          (backend)
    ├── users.json  votes.json  election.json  whitelist.json
    └── client/               <-- this folder
        ├── index.html
        ├── package.json
        ├── vite.config.js
        ├── public/icon.jpg
        └── src/
            ├── main.jsx
            ├── App.jsx       <-- the whole app
            └── styles.css    <-- your original styles.css, unchanged

## 1. Install Node.js
Node 20.19+ or 22+ is required by Vite 7. Check with:  node -v

## 2. Install backend dependencies (project root)
    npm install

## 3. Install frontend dependencies
    cd client
    npm install

This installs react, react-dom, @emailjs/browser, vite and @vitejs/plugin-react.

## 4. Run in development (two terminals)
Terminal 1 (project root):   node server.js     -> API on http://localhost:3000
Terminal 2 (client folder):  npm run dev        -> App on http://localhost:5173

Open http://localhost:5173

## 5. Production build (optional)
    cd client
    npm run build           -> creates client/dist

In server.js replace
    app.use(express.static(__dirname));
and the '/' route with
    app.use(express.static(path.join(__dirname, 'client', 'dist')));
    app.get('/', (req, res) => res.sendFile(path.join(__dirname, 'client', 'dist', 'index.html')));

Then `node server.js` serves everything on http://localhost:3000.

## Optional: EmailJS keys via environment
Create client/.env with:
    VITE_EMAILJS_PUBLIC_KEY=...
    VITE_EMAILJS_SERVICE_ID=...
    VITE_EMAILJS_TEMPLATE_ID=...
(If absent, the keys from your original script.js are used.)
