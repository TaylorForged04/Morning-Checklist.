<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Morning Checklist</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #008080;
            color: #fff;
            text-align: center;
            padding: 20px;
            position: relative;
        }
        .container {
            max-width: 400px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 10px;
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        li {
            background: #fff;
            color: #333;
            padding: 10px;
            margin: 5px 0;
            border-radius: 5px;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .completed {
            text-decoration: line-through;
            color: #666;
            position: relative;
        }
        .quote {
            position: absolute;
            top: 10px;
            right: 10px;
            font-size: 14px;
            color: black;
            max-width: 150px;
            text-align: right;
        }
        button {
            margin-top: 15px;
            padding: 10px;
            border: none;
            border-radius: 5px;
            background: #fff;
            color: #008080;
            cursor: pointer;
            font-size: 16px;
        }
        @keyframes confetti {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(-100px); opacity: 0; }
        }
        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background: yellow;
            opacity: 0;
            top: 50%;
            left: 50%;
            animation: confetti 1s ease-out;
        }
    </style>
</head>
<body>
    <div class="quote">“Success is the sum of small efforts repeated day in and day out.”</div>
    <div class="container">
        <h1>Morning Checklist</h1>
        <ul id="checklist">
            <li onclick="toggleItem(this)">Wake up at 7:00 AM <span></span></li>
            <li onclick="toggleItem(this)">Drink a glass of water <span></span></li>
            <li onclick="toggleItem(this)">Stretch for 5 minutes <span></span></li>
            <li onclick="toggleItem(this)">Read for 10 minutes <span></span></li>
            <li onclick="toggleItem(this)">Practice chess for 10 minutes <span></span></li>
            <li onclick="toggleItem(this)">Plan your tasks for the day <span></span></li>
        </ul>
        <button onclick="resetList()">Reset Checklist</button>
    </div>

    <script>
        function toggleItem(item) {
            item.classList.toggle('completed');
            const checkMark = item.querySelector('span');
            if (item.classList.contains('completed')) {
                checkMark.textContent = "✔";
                showConfetti();
            } else {
                checkMark.textContent = "";
            }
        }

        function resetList() {
            document.querySelectorAll('#checklist li').forEach(item => {
                item.classList.remove('completed');
                item.querySelector('span').textContent = "";
            });
        }

        function showConfetti() {
            for (let i = 0; i < 10; i++) {
                let confetti = document.createElement("div");
                confetti.className = "confetti";
                confetti.style.left = Math.random() * 100 + "vw";
                confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 50%)`;
                document.body.appendChild(confetti);
                setTimeout(() => confetti.remove(), 1000);
            }
        }
    </script>
</body>
</html>

