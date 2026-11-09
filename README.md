# The Daily Grind Server ☕

A simple Express.js server I built for a fictional coffee shop called **The Daily Grind**.

## What It Does

- Serves a homepage at `/`
- Serves a contact page at `/contact`
- Logs a confirmation message when the server starts

## Built With

- **Node.js** — runs JavaScript outside the browser
- **Express** — a lightweight framework for building servers
- **HTML** — for the two pages
- **Git + GitHub** — for version control and submission

## Getting Started

### Prerequisites

- Node.js installed (`node -v` should show a version)
- npm (comes with Node)

### Installation

1. Clone the repo:
    ```bash
    git clone https://github.com/YOUR-USERNAME/daily-grind-server.git
    ```
2. Go into the folder:
    ```bash
    cd daily-grind-server
    ```
3. Install dependencies:
    ```bash
    npm install
    ```
4. Start the server:
    ```bash
    node server.js
    ```
5. Open your browser
    - Homepage: http://localhost:3000/
    - Contact: http://localhost:3000/contact

6. Press `Ctrl + C` in the terminal to stop the server.

## Project Structure
```
daily-grind-server/
├── public/
│   ├── index.html      # homepage
│   └── contact.html    # contact page
├── node_modules/       # installed packages (not committed)
├── .gitignore          # tells Git to ignore node_modules
├── package.json        # project ID card + dependencies
├── package-lock.json   # exact package versions
├── server.js           # the Express server
└── README.md
```

## Reflection
1. What's the difference between `res.send()` and `res.sendFile()`?

`res.send()` sends data directly from code — like a string of HTML, plain text, or JSON. `res.sendFile()` sends an actual file from the disk. I'd use `send()` for small, dynamic responses and `sendFile()` for static HTML pages like the ones in this project.

2. Why do we need the `path` module? What could go wrong with a relative path?

`path.join()` builds a correct file path for whatever operating system the server runs on, and `__dirname` anchors it to the folder where `server.js` lives. If I used a relative path like `'public/index.html'`, Node would look relative to where I ran the command from — so running `node server.js` from a different folder would break the server. `path.join(__dirname, ...)` always points to the right place.

3. How would I add a menu page?

Three steps: (1) `create public/menu.html`, (2) add a route like `app.get('/menu', (req, res) => { res.sendFile(path.join(__dirname, 'public', 'menu.html')); })`, and (3) restart the server and test `http://localhost:3000/menu`.