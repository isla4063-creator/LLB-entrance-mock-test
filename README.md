# LLB-entrance-mock-test
Here is the complete HTML code ready to save as an .html file.
To download and run it:
 * Copy the code block below.
 * Open Notepad (Windows) or TextEdit (Mac).
 * Paste the code and save the file as index.html (select "All Files" as the file type).
 * Double-click index.html to open it in any web browser, or upload it to GitHub/Netlify to create your live test link.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Law Entrance - English Section Mock Test (100 Marks)</title>
  <style>
    :root {
      --primary: #0f172a;
      --secondary: #334155;
      --accent: #2563eb;
      --bg: #f1f5f9;
      --card-bg: #ffffff;
      --correct: #16a34a;
      --wrong: #dc2626;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: var(--bg);
      color: var(--primary);
      margin: 0;
      padding: 0;
    }

    .container {
      max-width: 900px;
      margin: 40px auto;
      background: var(--card-bg);
      border-radius: 12px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.05);
      padding: 30px;
    }

    h1 { text-align: center; color: var(--primary); font-size: 1.8rem; margin-bottom: 5px; }
    
    .exam-details {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin-bottom: 25px;
      color: #475569;
      font-weight: 500;
      flex-wrap: wrap;
    }
    
    .exam-details span {
      background: #e2e8f0;
      padding: 5px 12px;
      border-radius: 20px;
      font-size: 0.9rem;
    }

    .hidden { display: none !important; }

    /* Forms */
    .form-group { margin-bottom: 18px; }
    label { display: block; font-weight: 600; margin-bottom: 8px; }
    input[type="text"], input[type="email"] {
      width: 100%; padding: 12px; border: 1px solid #cbd5e1;
      border-radius: 6px; font-size: 1rem; box-sizing: border-box;
    }
    
    .btn {
      width: 100%; background: var(--accent); color: #fff;
      border: none; padding: 14px; border-radius: 6px;
      font-size: 1.1rem; font-weight: bold; cursor: pointer;
      transition: background 0.2s ease;
    }
    .btn:hover { background: #1d4ed8; }

    /* Sticky Header during Test */
    .test-header {
      position: sticky; top: 0; background: #fff; z-index: 100;
      display: flex; justify-content: space-between; align-items: center;
      padding: 15px 20px; border-bottom: 2px solid #e2e8f0;
      box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
      margin: -30px -30px 20px -30px;
      border-radius: 12px 12px 0 0;
    }
    .timer { font-size: 1.25rem; font-weight: bold; color: var(--wrong); }

    /* Sections & Questions */
    .section-title {
      background: var(--secondary); color: white;
      padding: 10px 15px; border-radius: 6px; margin: 30px 0 15px 0;
    }
    
    .question-card {
      border: 1px solid #e2e8f0; border-radius: 8px;
      padding: 20px; margin-bottom: 20px; background: #fafafa;
    }
    .q-title { font-weight: 600; margin-bottom: 15px; font-size: 1.05rem; }
    
    .option-label {
      display: flex; align-items: center; padding: 12px 15px;
      border: 1px solid #cbd5e1; border-radius: 6px; margin-bottom: 10px;
      background: #fff; cursor: pointer; transition: 0.2s;
    }
    .option-label:hover { border-color: var(--accent); background: #eff6ff; }
    .option-label input { margin-right: 15px; transform: scale(1.2); }

    /* Results */
    .score-board {
      text-align: center; background: #f0fdf4; border: 2px solid #bbf7d0;
      padding: 30px; border-radius: 12px; margin-bottom: 30px;
    }
    .score-number { font-size: 3.5rem; font-weight: bold; color: var(--correct); }
    .score-stats {
      display: flex; justify-content: space-around;
      margin-top: 15px; font-weight: bold; color: #475569;
    }
    .result-item {
      padding: 15px; border-radius: 6px; margin-bottom: 15px;
      border-left: 6px solid #cbd5e1; background: #fff; border-right: 1px solid #e2e8f0;
      border-top: 1px solid #e2e8f0; border-bottom: 1px solid #e2e8f0;
    }
    .result-item.correct { border-left-color: var(--correct); background: #f0fdf4; }
    .result-item.wrong { border-left-color: var(--wrong); background: #fef2f2; }
  </style>
</head>
<body>

<div class="container">
  <!-- REGISTRATION -->
  <div id="registration-section">
    <h1>English Language Mock Test</h1>
    <div class="exam-details">
      <span>⏱ 30 Mins</span>
      <span>📝 25 Questions</span>
      <span>✅ +4 Marks</span>
      <span>❌ -1 Negative</span>
      <span>Total: 100 Marks</span>
    </div>
    
    <form id="reg-form">
      <div class="form-group">
        <label>Full Name</label>
        <input type="text" id="student-name" required placeholder="Enter your full name">
      </div>
      <div class="form-group">
        <label>Email Address</label>
        <input type="email" id="student-email" required placeholder="Enter your email address">
      </div>
      <button type="submit" class="btn">Start Mock Exam</button>
    </form>
  </div>

  <!-- EXAM INTERFACE -->
  <div id="test-section" class="hidden">
    <div class="test-header">
      <div><strong>Candidate:</strong> <span id="disp-name"></span></div>
      <div class="timer">Time Left: <span id="time-disp">30:00</span></div>
    </div>
    <form id="quiz-form">
      <div id="questions-container"></div>
      <button type="button" class="btn" style="margin-top: 30px;" onclick="submitTest()">Final Submit Test</button>
    </form>
  </div>

  <!-- RESULTS -->
  <div id="result-section" class="hidden">
    <div class="score-board">
      <h2>Exam Submitted Successfully!</h2>
      <p><strong id="res-name"></strong> | <span id="res-email"></span></p>
      <div class="score-number"><span id="final-score">0</span><span style="font-size:1.5rem; color:#64748b;"> / 100</span></div>
      
      <div class="score-stats">
        <span style="color: var(--correct);">Correct: <span id="stat-correct">0</span></span>
        <span style="color: var(--wrong);">Incorrect: <span id="stat-wrong">0</span></span>
        <span>Unattempted: <span id="stat-unanswered">0</span></span>
      </div>
    </div>

    <h3>Detailed Performance Review</h3>
    <div id="review-container"></div>
  </div>
</div>

<script>
  const TIME_LIMIT_SECONDS = 30 * 60;
  const MARKS_CORRECT = 4;
  const MARKS_WRONG = 1;
  
  const questions = [
    {
      id: 1, section: "English Language",
      question: "Find the part of the sentence that contains an error: \nIf the policy were to be implemented nationwide (1)/ it would necessitate that every regional office (2)/ conducts a comprehensive audit (3)/ within a period of six months. (4)",
      options: ["1", "2", "3", "4"],
      correct: 2
    },
    {
      id: 2, section: "English Language",
      question: "Change the following from active to passive: \nThe tourists had taken many photographs.",
      options: [
        "Many photographs have been taken by the tourists.",
        "Many photographs are taken by the tourists.",
        "Many photographs had been taken by the tourists.",
        "Many photographs were being taken by the tourists."
      ],
      correct: 2
    },
    {
      id: 3, section: "English Language",
      question: "Select the sentence containing the homonym of the highlighted word: \nShe placed a **can** of soup on the shelf.",
      options: [
        "They opened a can of beans for lunch.",
        "He asked if she can lift 50 kg.",
        "The trash can was full.",
        "He ate pineapple from the can."
      ],
      correct: 1
    },
    {
      id: 4, section: "English Language",
      question: "Convert the sentence provided below from its passive voice structure to an active voice structure: \nThe investigation was believed to have been compromised by internal leaks.",
      options: [
        "The investigation compromised internal leaks, as believed.",
        "It was believed that internal leaks had compromised the investigation.",
        "Someone believed the investigation was compromising leaks.",
        "Internal leaks are believed to compromise the investigation."
      ],
      correct: 1
    },
    {
      id: 5, section: "English Language",
      question: "Choose the most suitable option to replace the highlighted part of the sentence: \nShe **conversed the matter with** me.",
      options: [
        "discussed the matter with",
        "talked over the matter with",
        "told the matter to",
        "said me about the matter"
      ],
      correct: 0
    },
    {
      id: 6, section: "English Language",
      question: "Choose the most suitable option to replace the highlighted part of the sentence: \nThe train was late **because of the heavy rain falls**.",
      options: [
        "due to the rain fall",
        "because of heavy rainfall",
        "owing to heavy rains",
        "as it rained heavily"
      ],
      correct: 1
    },
    {
      id: 7, section: "English Language",
      question: "Choose the option that represents the direct speech conversion of the sentence below: \nHe asserted that the cryptographic protocol might have resisted the attack had entropy been truly random.",
      options: [
        'He asserted, "Had entropy been truly random, the cryptographic protocol might have resisted the attack."',
        'He said, "If entropy is truly random, protocol might resist attack."',
        'He asserted, "If entropy had been random, protocol might resist attack."',
        'He said, "Entropy random, protocol resists attack."'
      ],
      correct: 0
    },
    {
      id: 8, section: "English Language",
      question: 'A sentence is provided in direct speech. From the four given options, choose the one that most accurately conveys the sentence in its corresponding indirect speech: \nHe asked, "Did you complete the homework?"',
      options: [
        "He asked whether I completed the homework.",
        "He asked if I had completed the homework.",
        "He asked did I completed the homework.",
        "He asked that I had completed the homework."
      ],
      correct: 1
    },
    {
      id: 9, section: "English Language",
      question: "Rearrange the following sentences in correct order to make a logical passage: \n1. The findings were analyzed to understand customer needs. \n2. The results were then shared with the development team. \n3. Based on the analysis, product enhancements were made. \n4. A survey was conducted to gather feedback from customers.",
      options: ["4-1-2-3", "1-2-4-3", "2-3-1-4", "3-4-1-2"],
      correct: 0
    },
    {
      id: 10, section: "English Language",
      question: "Rearrange the following sentences in correct order to make a logical passage: \n1. A strategy was developed to address key market challenges. \n2. Market research was conducted to identify trends. \n3. Insights from research were used to finalize the strategy. \n4. The strategy was then implemented in phases.",
      options: ["2-3-1-4", "1-3-2-4", "3-2-1-4", "4-1-3-2"],
      correct: 0
    },
    {
      id: 11, section: "English Language",
      question: "Select the most appropriate synonym of the given word: ANACHRONISTIC",
      options: ["Modern", "Futuristic", "Timely", "Outdated"],
      correct: 3
    },
    {
      id: 12, section: "English Language",
      question: "Select the most appropriate antonym of the given word: PROSAIC",
      options: ["Imaginative", "Banal", "Ordinary", "Dull"],
      correct: 0
    },
    {
      id: 13, section: "English Language",
      question: "Choose the correct meaning of the idiom: Go for a song",
      options: ["Sold at a high price", "Performed emotionally", "Sold very cheaply", "Sung badly"],
      correct: 2
    },
    {
      id: 14, section: "English Language",
      question: "Choose the correct meaning of the idiom: Not to mince matters",
      options: ["To speak delicately", "To speak without hesitation or euphemism", "To avoid detail intentionally", "To revise opinions often"],
      correct: 1
    },
    {
      id: 15, section: "English Language",
      question: "Select the correctly spelt word.",
      options: ["Accomodate", "Accommodate", "Acommodate", "Accommodat"],
      correct: 1
    },
    {
      id: 16, section: "English Language",
      question: "Choose the correct one-word substitute for: 'An animal that feeds on both plants and animals'.",
      options: ["Herbivore", "Carnivore", "Omnivore", "Scavenger"],
      correct: 2
    },
    {
      id: 17, section: "English Language",
      question: "Choose the correct tense: By next year, she ______ completed her research.",
      options: ["will be", "has", "will have", "had"],
      correct: 2
    },
    {
      id: 18, section: "English Language",
      question: "Select the most appropriate antonym of the given word: EPHEMERAL",
      options: ["Transient", "Permanent", "Fleeting", "Short-lived"],
      correct: 1
    },
    {
      id: 19, section: "English Language",
      question: "Choose the correct meaning of the idiom: 'To burn the midnight oil'",
      options: ["To waste resources", "To work or study late into the night", "To cause an accident", "To burn old items"],
      correct: 1
    },
    {
      id: 20, section: "English Language",
      question: "Fill in the blank: Neither the teacher nor the students ______ present in the seminar hall.",
      options: ["was", "were", "is", "has been"],
      correct: 1
    },
    {
      id: 21, section: "English Language",
      question: "Choose the correct one-word substitute for: 'A person who looks at the bright side of things.'",
      options: ["Pessimist", "Optimist", "Pacifist", "Altruist"],
      correct: 1
    },
    {
      id: 22, section: "English Language",
      question: "Identify the correct synonym of the given word: CANDID",
      options: ["Secretive", "Frank", "Deceitful", "Shy"],
      correct: 1
    },
    {
      id: 23, section: "English Language",
      question: "Choose the correct meaning of the idiom: 'A blessing in disguise'",
      options: ["A good thing that seemed bad at first", "A curse", "Something very expensive", "A hidden enemy"],
      correct: 0
    },
    {
      id: 24, section: "English Language",
      question: "Fill in the blank: She is senior ______ me in the organization.",
      options: ["than", "to", "from", "with"],
      correct: 1
    },
    {
      id: 25, section: "English Language",
      question: "Select the antonym for the word: OPAQUE",
      options: ["Transparent", "Cloudy", "Hazy", "Dark"],
      correct: 0
    }
  ];

  let studentData = { name: "", email: "" };
  let timerInterval;
  let timeRemaining = TIME_LIMIT_SECONDS;

  document.getElementById('reg-form').addEventListener('submit', function(e) {
    e.preventDefault();
    studentData.name = document.getElementById('student-name').value;
    studentData.email = document.getElementById('student-email').value;

    document.getElementById('registration-section').classList.add('hidden');
    document.getElementById('test-section').classList.remove('hidden');
    document.getElementById('disp-name').textContent = studentData.name;

    renderQuestions();
    startTimer();
  });

  function renderQuestions() {
    const container = document.getElementById('questions-container');
    let currentSection = "";
    let html = "";

    questions.forEach((q) => {
      if (q.section !== currentSection) {
        html += `<h2 class="section-title">${q.section}</h2>`;
        currentSection = q.section;
      }

      html += `
        <div class="question-card">
          <div class="q-title">Q${q.id}. ${q.question.replace(/\n/g, '<br>')}</div>
          ${q.options.map((opt, oIdx) => `
            <label class="option-label">
              <input type="radio" name="q_${q.id}" value="${oIdx}">
              <span>${opt}</span>
            </label>
          `).join('')}
        </div>
      `;
    });
    container.innerHTML = html;
  }

  function startTimer() {
    timerInterval = setInterval(() => {
      timeRemaining--;
      let mins = Math.floor(timeRemaining / 60);
      let secs = timeRemaining % 60;
      document.getElementById('time-disp').textContent = 
        `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;

      if (timeRemaining <= 0) {
        clearInterval(timerInterval);
        submitTest();
      }
    }, 1000);
  }

  function submitTest() {
    clearInterval(timerInterval);
    let score = 0;
    let correctCount = 0, wrongCount = 0, unattemptedCount = 0;
    let reviewHtml = '';

    questions.forEach(q => {
      const selected = document.querySelector(`input[name="q_${q.id}"]:checked`);
      let statusClass = 'unanswered';
      let userChoiceText = 'Unattempted';

      if (!selected) {
        unattemptedCount++;
      } else {
        const val = parseInt(selected.value);
        userChoiceText = q.options[val];
        if (val === q.correct) {
          score += MARKS_CORRECT;
          correctCount++;
          statusClass = 'correct';
        } else {
          score -= MARKS_WRONG;
          wrongCount++;
          statusClass = 'wrong';
        }
      }

      reviewHtml += `
        <div class="result-item ${statusClass}">
          <strong>Q${q.id}: ${q.question.replace(/\n/g, '<br>')}</strong><br><br>
          <div style="color: #475569;">Your Answer: <em>${userChoiceText}</em></div>
          <div style="color: #16a34a; margin-top: 5px;">Correct Answer: <strong>${q.options[q.correct]}</strong></div>
        </div>
      `;
    });

    document.getElementById('test-section').classList.add('hidden');
    document.getElementById('result-section').classList.remove('hidden');
    window.scrollTo(0, 0);

    document.getElementById('res-name').textContent = studentData.name;
    document.getElementById('res-email').textContent = studentData.email;
    document.getElementById('final-score').textContent = score;
    
    document.getElementById('stat-correct').textContent = correctCount;
    document.getElementById('stat-wrong').textContent = wrongCount;
    document.getElementById('stat-unanswered').textContent = unattemptedCount;
    
    document.getElementById('review-container').innerHTML = reviewHtml;
  }
</script>

</body>
</html>

