<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Website.Supply SEO Tracker</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(to right, #4b6cb7, #182848);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            color: #fff;
        }

        .navbar {
            background-color: #2c3e50;
            overflow: hidden;
            position: fixed;
            top: 0;
            width: 100%;
        }

        .navbar a {
            float: left;
            display: block;
            color: #ecf0f1;
            text-align: center;
            padding: 14px 16px;
            text-decoration: none;
            font-size: 17px;
        }

        .navbar a:hover {
            background-color: #3498db;
            color: #2c3e50;
        }

        .navbar a.active {
            background-color: #e74c3c;
            color: white;
        }

        .tracker {
            background: rgba(255, 255, 255, 0.1);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            width: 350px;
            margin-top: 50px;
        }

        h2 {
            color: #e74c3c;
            margin-bottom: 1.5rem;
            text-align: center;
        }

        .input-group {
            margin-bottom: 1rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            color: #ecf0f1;
        }

        input[type="url"], input[type="text"], select, button {
            width: 100%;
            padding: 10px;
            border: none;
            border-radius: 5px;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            font-size: 16px;
        }

        button {
            background: #e74c3c;
            color: #fff;
            cursor: pointer;
            transition: background 0.3s;
        }

        button:hover {
            background: #c0392b;
        }

        #results {
            text-align: center;
            margin-top: 20px;
            color: #ecf0f1;
        }
    </style>
</head>
<body>

<div class="navbar">
    <a href="#home" class="active">Home</a>
    <a href="#tracker">SEO Tracker</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
</div>

<div class="tracker">
    <h2>SEO Position Tracker</h2>
    <div class="input-group">
        <label for="website">Website URL:</label>
        <input type="url" id="website" placeholder="Enter your website URL">
    </div>
    <div class="input-group">
        <label for="keywords">Keywords:</label>
        <input type="text" id="keywords" placeholder="Enter keywords separated by commas">
    </div>
    <div class="input-group">
        <label for="searchEngine">Search Engine:</label>
        <select id="searchEngine">
            <option value="google">Google</option>
            <option value="bing">Bing</option>
        </select>
    </div>
    <button onclick="trackPositions()">Track SEO</button>
    <div id="results">
        <p>Your SEO rankings will show here.</p>
    </div>
</div>

<script>
function trackPositions() {
    // Placeholder for tracking logic
    const website = document.getElementById('website').value;
    const keywords = document.getElementById('keywords').value.split(',').map(keyword => keyword.trim());
    const resultsDiv = document.getElementById('results');
    resultsDiv.innerHTML = `<p>Tracking in progress for ${website}...</p>`;
    // Here would go the actual call to an API or function to fetch SEO positions
    // For now, we'll simulate with a random rank
    setTimeout(() => {
        let output = '<h3>Rankings:</h3><ul>';
        keywords.forEach(keyword => {
            output += `<li>${keyword}: Rank ${Math.floor(Math.random() * 100) + 1}</li>`;
        });
        output += '</ul>';
        resultsDiv.innerHTML = output;
    }, 1500);
}
</script>

</body>
</html>