# Mlbb-pro
// File: src/main.jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import MPLGameMainMenu from './MPLGameMainMenu';

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <MPLGameMainMenu />
  </React.StrictMode>
);


// File: src/MPLGameMainMenu.jsx
import { useState } from 'react';

export default function MPLGameMainMenu() {
  const [playerName, setPlayerName] = useState('');
  const [nickname, setNickname] = useState('');
  const [role, setRole] = useState('Jungle');
  const [started, setStarted] = useState(false);

  const roles = ['Jungle', 'Mid', 'EXP Lane', 'Gold Lane', 'Roam'];

  if (started) {
    return (
      <div className="main-container">
        <h2>Welcome, {nickname}!</h2>
        <p>Role: {role}</p>
        <p>You’re ready to start your MPL journey.</p>
        <button onClick={() => setStarted(false)}>Back to Menu</button>
      </div>
    );
  }

  return (
    <div className="main-container">
      <h1>MPL: Rise of BONCHIK</h1>
      <input
        placeholder="Enter your full name"
        value={playerName}
        onChange={(e) => setPlayerName(e.target.value)}
      />
      <input
        placeholder="Enter your nickname (e.g. BONCHIK)"
        value={nickname}
        onChange={(e) => setNickname(e.target.value)}
      />
      <label>Choose Your Role:</label>
      <select value={role} onChange={(e) => setRole(e.target.value)}>
        {roles.map((r) => (
          <option key={r} value={r}>{r}</option>
        ))}
      </select>
      <button onClick={() => setStarted(true)}>Start Your Career</button>
    </div>
  );
}


// File: src/index.css
body {
  font-family: Arial, sans-serif;
  background: #1e1e2f;
  color: white;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  padding: 2rem;
  min-height: 100vh;
}
.main-container {
  max-width: 400px;
  width: 100%;
  background: #2d2d44;
  padding: 20px;
  border-radius: 10px;
}
input, select, button {
  width: 100%;
  padding: 10px;
  margin: 0.5rem 0;
  border-radius: 5px;
  border: none;
}
button {
  background: #ffd600;
  color: #000;
  font-weight: bold;
  cursor: pointer;
}


// File: index.html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>MPL: Rise of BONCHIK</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>


// File: vite.config.js
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
});


// File: package.json
{
  "name": "mpl-rise-of-bonchik",
  "version": "1.0.0",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.0.0",
    "react-dom": "^18.0.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.0.0",
    "vite": "^4.0.0"
  }
}
