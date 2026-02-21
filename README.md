<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Daily Spiritual Organization</title>
    <style>
        :root {
            --primary-color: #2c3e50;
            --accent-color: #27ae60;
            --bg-color: #f4f7f6;
            --card-bg: #ffffff;
            --text-color: #333;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 1000px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        /* Header / Clock Section */
        .header-section {
            grid-column: 1 / -1;
            background: var(--primary-color);
            color: white;
            padding: 20px;
            border-radius: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .time-display {
            font-size: 2rem;
            font-weight: bold;
        }

        .date-display {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        /* Cards */
        .card {
            background: var(--card-bg);
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
            display: flex;
            flex-direction: column;
        }

        .card h2 {
            margin-bottom: 15px;
            color: var(--primary-color);
            border-bottom: 2px solid var(--bg-color);
            padding-bottom: 10px;
            font-size: 1.2rem;
        }

        /* Prayer Section */
        .prayer-list {
            list-style: none;
        }

        .prayer-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px solid #eee;
        }

        .prayer-item label {
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .prayer-item input[type="checkbox"] {
            width: 20px;
            height: 20px;
            accent-color: var(--accent-color);
            cursor: pointer;
        }

        .completed {
            text-decoration: line-through;
            color: #aaa;
        }

        /* Lesson Section */
        .input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
        }

        input[type="text"] {
            flex-grow: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            outline: none;
        }

        button#addLessonBtn {
            padding: 10px 15px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
        }

        button#addLessonBtn:hover {
            background-color: #34495e;
        }

        #lessonList {
            list-style: none;
            overflow-y: auto;
            max-height: 250px;
        }

        .lesson-item {
            background: #f9f9f9;
            padding: 10px;
            margin-bottom: 8px;
            border-radius: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .delete-btn {
            color: red;
            cursor: pointer;
            font-weight: bold;
            margin-left: 10px;
        }

        /* Daily Quote */
        .quote-section {
            grid-column: 1 / -1;
            text-align: center;
            font-style: italic;
            color: #555;
            background: #e8f6f3;
            padding: 15px;
            border-radius: 10px;
            border-left: 5px solid var(--accent-color);
        }

        @media (max-width: 600px) {
            .header-section {
                flex-direction: column;
                text-align: center;
                gap: 10px;
            }
        }
    </style>
</head>
<body>

    <div class="container">
        
        <!-- Time and Date -->
        <div class="header-section">
            <div class="date-display" id="dateDisplay">Loading Date...</div>
            <div class="time-display" id="clock">00:00:00</div>
        </div>

        <!-- Prayer / Spiritual Tracker -->
        <div class="card">
            <h2>🙏 Spiritual (Prayers)</h2>
            <ul class="prayer-list">
                <li class="prayer-item">
                    <label>
                        <input type="checkbox" onchange="toggleText(this)"> 
                        Fajr / Morning Prayer
                    </label>
                </li>
                <li class="prayer-item">
                    <label>
                        <input type="checkbox" onchange="toggleText(this)"> 
                        Dhuhr / Midday Prayer
                    </label>
                </li>
                <li class="prayer-item">
                    <label>
                        <input type="checkbox" onchange="toggleText(this)"> 
                        Asr / Afternoon Prayer
                    </label>
                </li>
                <li class="prayer-item">
                    <label>
                        <input type="checkbox" onchange="toggleText(this)"> 
                        Maghrib / Evening Prayer
                    </label>
                </li>
                <li class="prayer-item">
                    <label>
                        <input type="checkbox" onchange="toggleText(this)"> 
                        Isha / Night Prayer
                    </label>
                </li>
            </ul>
        </div>

        <!-- Lessons / Study Plan -->
        <div class="card">
            <h2>📖 Today's Lessons</h2>
            <div class="input-group">
                <input type="text" id="lessonInput" placeholder="Enter lesson topic (e.g., Quran Tafsir)...">
                <button id="addLessonBtn">Add</button>
            </div>
            <ul id="lessonList">
                <!-- Lessons will appear here -->
            </ul>
        </div>

        <!-- Daily Schedule / Tasks -->
        <div class="card">
            <h2>📝 Daily Tasks</h2>
            <ul class="prayer-list">
                <li class="prayer-item">
                    <label><input type="checkbox" onchange="toggleText(this)"> Review Notes</label>
                </li>
                <li class="prayer-item">
                    <label><input type="checkbox" onchange="toggleText(this)"> DO H.W</label>
                </li>
                <li class="prayer-item">
                    <label><input type="checkbox" onchange="toggleText(this)"> STUDY Lesson</label>
                </li>
            </ul>
        </div>

        <!-- Motivational Quote -->
        <div class="quote-section">
            "Indeed, those who have believed and done righteous deeds - the Most Merciful will appoint for them affection."
            <br><small>(Surah Maryam 19:96)</small>
        </div>

    </div>

    <script>
        // --- 1. Clock and Date Functionality ---
        function updateTime() {
            const now = new Date();
            
            // Time
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const seconds = String(now.getSeconds()).padStart(2, '0');
            document.getElementById('clock').innerText = `${hours}:${minutes}:${seconds}`;

            // Date
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            document.getElementById('dateDisplay').innerText = now.toLocaleDateString('en-US', options);
        }
        setInterval(updateTime, 1000);
        updateTime(); // Run immediately

        // --- 2. Checklist Logic ---
        function toggleText(checkbox) {
            if (checkbox.checked) {
                checkbox.parentElement.classList.add('completed');
            } else {
                checkbox.parentElement.classList.remove('completed');
            }
        }

        // --- 3. Lesson List Logic (Add/Delete) ---
        const addBtn = document.getElementById('addLessonBtn');
        const lessonInput = document.getElementById('lessonInput');
        const lessonList = document.getElementById('lessonList');

        addBtn.addEventListener('click', addLesson);
        
        // Allow pressing "Enter" key
        lessonInput.addEventListener('keypress', function (e) {
            if (e.key === 'Enter') {
                addLesson();
            }
        });

        function addLesson() {
            const text = lessonInput.value;
            if (text === '') return;

            // Create List Item
            const li = document.createElement('li');
            li.className = 'lesson-item';
            
            li.innerHTML = `
                <span>${text}</span>
                <span class="delete-btn" onclick="this.parentElement.remove()">✖</span>
            `;

            lessonList.appendChild(li);
            lessonInput.value = ''; // Clear input
        }
    </script>
</body>
</html>
