# generator
#html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Daily Quote & Reflection</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>🌞 Daily Quote & Reflection</h1>
    <div class="quote-box">
      <p id="quote">Loading quote...</p>
      <span id="author"></span>
    </div>

    <textarea
      id="reflection"
      placeholder="Write your thoughts here..."
      rows="8"
    ></textarea>

    <button onclick="saveReflection()">💾 Save Reflection</button>
    <p id="status"></p>
  </div>

  <script src="script.js"></script>
</body>
</html>
#css
body {
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(135deg, #f5f7fa, #c3cfe2);
  color: #333;
  padding: 40px;
  display: flex;
  justify-content: center;
}

.container {
  max-width: 600px;
  background: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.quote-box {
  background-color: #eef2f3;
  border-left: 5px solid #3f51b5;
  padding: 15px 20px;
  margin-bottom: 20px;
  border-radius: 8px;
}

#quote {
  font-style: italic;
  font-size: 18px;
}

#author {
  display: block;
  text-align: right;
  margin-top: 10px;
  font-weight: bold;
}

textarea {
  width: 100%;
  border: 1px solid #ccc;
  padding: 12px;
  border-radius: 8px;
  resize: vertical;
  font-size: 16px;
}

button {
  margin-top: 15px;
  padding: 10px 20px;
  background-color: #3f51b5;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: #2c3e9f;
}

#status {
  margin-top: 10px;
  font-size: 14px;
  color: green;
}
#java script
// Simple quote list (you can add more)
const quotes = [
  { text: "The best way to predict the future is to create it.", author: "Peter Drucker" },
  { text: "Do what you can, with what you have, where you are.", author: "Theodore Roosevelt" },
  { text: "Happiness is not something ready made. It comes from your own actions.", author: "Dalai Lama" },
  { text: "It always seems impossible until it’s done.", author: "Nelson Mandela" },
  { text: "Believe you can and you're halfway there.", author: "Theodore Roosevelt" }
];

// Get today's date in YYYY-MM-DD
const today = new Date().toISOString().split("T")[0];

// Elements
const quoteEl = document.getElementById("quote");
const authorEl = document.getElementById("author");
const reflectionEl = document.getElementById("reflection");
const statusEl = document.getElementById("status");

// Load quote
function loadQuote() {
  const seed = new Date().getDate(); // Change daily
  const quote = quotes[seed % quotes.length];
  quoteEl.textContent = "${quote.text}";
  authorEl.textContent = — ${quote.author};
}

// Load reflection from localStorage
function loadReflection() {
  const saved = localStorage.getItem(reflection-${today});
  if (saved) reflectionEl.value = saved;
}

// Save reflection
function saveReflection() {
  const text = reflectionEl.value.trim();
  localStorage.setItem(reflection-${today}, text);
  statusEl.textContent = "✅ Reflection saved!";
  setTimeout(() => (statusEl.textContent = ""), 2000);
}

// Initialize
loadQuote();
loadReflection();
