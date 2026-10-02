<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>APX Digital - Course App</title>
    <style>
        :root {
            --apx-red: #d32f2f;
            --apx-dark: #121212;
            --apx-gold: #d4af37;
            --bg-light: #f7f9fa;
        }
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            margin: 0; padding: 0; background-color: var(--bg-light); color: #333;
        }
        /* 📱 Light App Header Banner */
        .app-bar {
            background: linear-gradient(135deg, var(--apx-dark) 0%, #2c0000 100%);
            color: white; text-align: center; padding: 18px;
            border-bottom: 3px solid var(--apx-gold);
            box-shadow: 0 4px 8px rgba(0,0,0,0.15);
        }
        .app-bar h1 { margin: 0; font-size: 24px; color: #fff; letter-spacing: 2px; font-weight: 800; }
        .app-bar h1 span { color: var(--apx-gold); }
        .app-bar p { margin: 4px 0 0 0; font-size: 12px; color: #ccc; letter-spacing: 1px; }

        .container { padding: 15px; max-width: 500px; margin: 0 auto; box-sizing: border-box; }

        /* 🔄 Navigation Menu Items */
        .nav-tabs { display: flex; gap: 6px; margin-bottom: 20px; }
        .tab-link {
            background: #e0e0e0; color: #444; padding: 12px 5px; border: none;
            border-radius: 8px; font-size: 13px; font-weight: bold; cursor: pointer;
            flex: 1; text-align: center; transition: 0.2s;
        }
        .tab-link.active { background: var(--apx-red); color: white; }

        /* 📑 App Windows Pages Content views */
        .page-card {
            background: white; border-radius: 12px; padding: 18px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05); margin-bottom: 25px;
        }
        .page-title { font-size: 18px; font-weight: bold; color: var(--apx-red); margin-bottom: 15px; border-bottom: 2px solid #ffcdbe; padding-bottom: 5px; }

        /* Course Cards Layout */
        .course-item {
            background: #fff8f8; border: 1px solid #ffcdbe; border-radius: 8px;
            padding: 15px; margin-bottom: 12px; cursor: pointer;
        }
        .course-name { font-weight: bold; font-size: 16px; color: var(--apx-dark); }
        .course-meta { font-size: 12px; color: #666; margin-top: 4px; display: flex; justify-content: space-between;}

        /* Form input fields */
        .form-group { display: flex; flex-direction: column; gap: 6px; margin-bottom: 14px; }
        .form-group label { font-weight: bold; font-size: 14px; color: #444; }
        .form-group textarea {
            padding: 12px; border: 1px solid #ccc; border-radius: 8px; font-size: 15px; outline: none; resize: none; height: 120px;
        }
        .btn {
            background-color: var(--apx-red); color: white; width: 100%; padding: 12px;
            border: none; border-radius: 8px; font-size: 15px; font-weight: bold; cursor: pointer;
        }
        .btn:active { background-color: #b71c1c; }

        /* Saved Notes Log Grid styles */
        .note-log {
            background: #f9f9f9; padding: 12px; border-radius: 6px; margin-top: 10px;
            border-left: 4px solid var(--apx-gold); font-size: 14px; line-height: 1.5;
        }
        
        .hidden { display: none; }
    </style>
</head>
<body>

    <!-- 👑 APX Digital Premium Branding Header -->
    <div class="app-bar">
        <h1>APX <span>DIGITAL</span></h1>
        <p>⚡ LIGHTWEIGHT LEARNING APP ⚡</p>
    </div>

    <div class="container">
        
        <!-- 🔄 3 Main Features Controller Tabs Menu -->
        <div class="nav-tabs">
            <button class="tab-link active" id="tab-course" onclick="openModule('course')">📚 Courses</button>
            <button class="tab-link" id="tab-notes" onclick="openModule('notes')">📝 Study Notes</button>
            <button class="tab-link" id="tab-profile" onclick="openModule('profile')">👤 My Dashboard</button>
        </div>

        <!-- 📄 MODULE 1: AVAILABLE COURSES SCREEN LIST -->
        <div id="view-course" class="page-card">
            <div class="page-title">Explore Premium Digital Courses</div>
            
            <div class="course-item" onclick="alert('Digital Marketing Course Launching Soon!')">
                <div class="course-name">🚀 Full Stack Digital Marketing</div>
                <div class="course-meta"><span>Modules: 24 Videos</span> <span style="color:var(--apx-red); font-weight:bold;">FREE</span></div>
            </div>

            <div class="course-item" onclick="alert('Web Development Course Launching Soon!')">
                <div class="course-name">💻 HTML, CSS & JS Website Designing</div>
                <div class="course-meta"><span>Modules: 32 Videos</span> <span style="color:var(--apx-red); font-weight:bold;">FREE</span></div>
            </div>

            <div class="course-item" onclick="alert('Android App Development Course Launching Soon!')">
                <div class="course-name">📱 Mobile App Development (Light Apps)</div>
                <div class="course-meta"><span>Modules: 18 Videos</span> <span style="color:var(--apx-red); font-weight:bold;">FREE</span></div>
            </div>
        </div>

        <!-- 📄 MODULE 2: INTERACTIVE WRITING STUDY NOTES PAD -->
        <div id="view-notes" class="page-card hidden">
            <div class="page-title">Personal Smart Study Notepad</div>
            <div class="form-group">
                <label>Type Your Daily Lecture Notes Below:</label>
                <textarea id="noteContentText" placeholder="Aaj aapne class me kya seekha? Yahan note karein aur save karein..."></textarea>
            </div>
            <button class="btn" onclick="saveStudyNote()">Save Lecture Note</button>

            <div class="page-title" style="margin-top: 25px; font-size: 15px;">Saved Notes History</div>
            <div id="historyNotesBox"></div>
        </div>

        <!-- 📄 MODULE 3: PROFILE CONTROLLERS DASHBOARD PANEL -->
        <div id="view-profile" class="page-card hidden">
            <div class="page-title">Student Portal Status Dashboard</div>
            <div style="text-align: center; padding: 10px 0;">
                <div style="width: 70px; height: 70px; background: var(--apx-red); color: white; font-size: 30px; font-weight: bold; border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto 10px auto; border: 3px solid var(--apx-gold);">A</div>
                <h3 style="margin: 0; color: var(--apx-dark);">Anuj Kumar</h3>
                <p style="margin: 5px 0; font-size: 13px; color: #666;">Course Student ID: APX-2026-89</p>
            </div>
            <hr style="border: 0; border-top: 1px solid #eee; margin: 15px 0;">
            <div style="font-size: 14px; line-height: 2;">
                <div><strong>Current Active Course:</strong> Mobile App Coding</div>
                <div><strong>Learning Progress:</strong> 85% Completed</div>
                <div><strong>Current Rank Points:</strong> 420 XP</div>
            </div>
        </div>

    </div>

    <script>
        // System initial configuration memory loads on boot launch
        window.onload = function() {
            renderSavedNotes();
        };

        // Navigation module manager layout switcher routing engine
        function openModule(moduleName) {
            document.getElementById('tab-course').classList.remove('active');
            document.getElementById('tab-notes').classList.remove('active');
            document.getElementById('tab-profile').classList.remove('active');

            document.getElementById('view-course').classList.add('hidden');
            document.getElementById('view-notes').classList.add('hidden');
            document.getElementById('view-profile').classList.add('hidden');

            if(moduleName === 'course') {
                document.getElementById('tab-course').classList.add('active');
                document.getElementById('view-course').classList.remove('hidden');
            } else if(moduleName === 'notes') {
                document.getElementById('tab-notes').classList.add('active');
                document.getElementById('view-notes').classList.remove('hidden');
                renderSavedNotes();
            } else if(moduleName === 'profile') {
                document.getElementById('tab-profile').classList.add('active');
                document.getElementById('view-profile').classList.remove('hidden');
            }
        }

        // Action Function: Saves notepad lines automatically inside phone offline storage maps
        function saveStudyNote() {
            const content = document.getElementById('noteContentText').value.trim();
            if(!content) {
                alert("⚠️ Kripya note khali mat chhodiye, kuch type karke save karein!");
                return;
            }

            const now = new Date();
            const timeStr = now.toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit', hour12: true });
            const dateStr = now.toLocaleDateString('en-US', { day: '2-digit', month: 'short', year: 'numeric' });

            const noteObject = {
                id: Date.now(),
                text: content,
                time: timeStr,
                date: dateStr
            };

            let notesPool = JSON.parse(localStorage.getItem('apx_digital_notes')) || [];
            notesPool.unshift(noteObject); // Put newest items on top row logs grid
            localStorage.setItem('apx_digital_notes', JSON.stringify(notesPool));

            // ✨ THE BLANK NEW PAGE RESET EFFECT: clear notepad instantly
            document.getElementById('noteContentText').value = "";
            renderSavedNotes();
            alert("🎉 Lecture Note automatic save ho gaya hai!");
        }

        // Render functions for displaying saved notes list items on bottom grids sheet layout
        
