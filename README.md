<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dallas ISD Depth & Complexity Deck</title>
  <style>
    :root {
      --primary: #003366;
      --secondary: #008080;
      --accent: #ff9900;
      --bg: #f4f6f9;
      --card-bg: #ffffff;
      --text: #333333;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: var(--bg);
      color: var(--text);
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    header {
      background-color: var(--primary);
      color: white;
      padding: 1rem 1.5rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    header h1 {
      margin: 0;
      font-size: 1.1rem;
    }

    .badge {
      background-color: var(--accent);
      color: white;
      padding: 0.3rem 0.8rem;
      border-radius: 20px;
      font-weight: bold;
      font-size: 0.85rem;
    }

    main {
      flex: 1;
      max-width: 850px;
      width: 100%;
      margin: 1.5rem auto;
      padding: 0 1rem;
      box-sizing: border-box;
    }

    .slide-card {
      background-color: var(--card-bg);
      border-radius: 8px;
      padding: 2rem;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
    }

    .slide-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 2px solid var(--bg);
      padding-bottom: 0.8rem;
      margin-bottom: 1.2rem;
    }

    .slide-title {
      color: var(--primary);
      margin: 0;
      font-size: 1.4rem;
    }

    .slide-body {
      font-size: 1.1rem;
      line-height: 1.6;
      margin-bottom: 1.5rem;
    }

    .presenter-note {
      background-color: #f0f4f8;
      border-left: 4px solid var(--primary);
      padding: 0.8rem 1rem;
      font-size: 0.95rem;
      color: #555;
      margin-bottom: 1.5rem;
      border-radius: 0 4px 4px 0;
    }

    .activity-container {
      background-color: #eef7f7;
      border: 2px solid var(--secondary);
      border-radius: 8px;
      padding: 1.5rem;
      margin-top: 1.5rem;
    }

    .activity-container h3 {
      margin-top: 0;
      color: var(--secondary);
    }

    /* Interactive Element Styles */
    .btn-group {
      display: flex;
      gap: 10px;
      margin-top: 1rem;
      flex-wrap: wrap;
    }

    button.act-btn {
      flex: 1;
      min-width: 120px;
      padding: 0.8rem 1rem;
      border: 2px solid var(--primary);
      background-color: white;
      color: var(--primary);
      border-radius: 6px;
      font-size: 1rem;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.2s;
    }

    button.act-btn:hover, button.act-btn.selected {
      background-color: var(--primary);
      color: white;
    }

    .scale-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 10px;
      margin-top: 1rem;
    }

    .scale-btn {
      padding: 1rem;
      border: 2px solid var(--secondary);
      border-radius: 8px;
      background: white;
      color: var(--secondary);
      font-weight: bold;
      cursor: pointer;
      text-align: left;
    }

    .scale-btn:hover, .scale-btn.selected {
      background-color: var(--secondary);
      color: white;
    }

    textarea {
      width: 100%;
      height: 80px;
      padding: 0.6rem;
      margin-top: 0.5rem;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
      font-family: inherit;
    }

    .corners-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      margin-top: 1rem;
    }

    .corner-card {
      border: 2px dashed #ccc;
      padding: 1rem;
      border-radius: 8px;
      text-align: center;
      cursor: pointer;
      background: white;
    }

    .corner-card.selected {
      border-color: var(--accent);
      background-color: #fff8ee;
    }

    /* Navigation Bar */
    .nav-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 1.5rem;
    }

    .nav-btn {
      background-color: var(--primary);
      color: white;
      border: none;
      padding: 0.8rem 1.5rem;
      border-radius: 6px;
      font-weight: bold;
      cursor: pointer;
      font-size: 1rem;
    }

    .nav-btn:disabled {
      background-color: #ccc;
      cursor: not-allowed;
    }

    .progress-text {
      font-weight: bold;
      color: var(--primary);
    }
  </style>
</head>
<body>

  <header>
    <h1>Dallas ISD: Depth & Complexity Workshop</h1>
    <span class="badge" id="assigned-badge">Icon #1: Patterns</span>
  </header>

  <main>
    <div class="slide-card">
      <div class="slide-header">
        <h2 class="slide-title" id="slide-title">Slide Title</h2>
        <span class="progress-text" id="slide-progress">Slide 1 of 25</span>
      </div>

      <div class="slide-body" id="slide-content">
        <!-- Slide content renders here -->
      </div>

      <div class="presenter-note" id="slide-note">
        <!-- Facilitator note renders here -->
      </div>

      <!-- Interactive Pause Point Activity Slot -->
      <div class="activity-container" id="activity-box" style="display: none;">
        <!-- Dynamic Activity Controls Render Here -->
      </div>

      <div class="nav-bar">
        <button class="nav-btn" id="prev-btn" onclick="navigateSlide(-1)">Previous</button>
        <button class="nav-btn" id="next-btn" onclick="navigateSlide(1)">Next Slide</button>
      </div>
    </div>
  </main>

  <script>
    // 25-Slide Deck Data with Embedded Pause Points
    const deck = [
      {
        title: "Depth and Complexity in the Curriculum",
        content: "<p>In our Dallas ISD curriculum, we use the <strong>Instructional Planning Calendar (IPC)</strong> to see where these opportunities live. Looking at your IPC for Quarter 1, you'll see Eureka Math lessons, concrete experiences, and engagement strategies mapped out. We want to identify where we can 'up the ante' using Universal Design for Learning and Depth and Complexity icons.</p>",
        note: "SAY: Let's take a closer look at these lessons to identify where we can deepen student understanding.",
        activityType: null
      },
      {
        title: "Energizer: Thinking Beyond the Word",
        content: "<p>Select either <strong>'depth'</strong> or <strong>'complexity'</strong>. As a group, construct a definition for the term by writing every word, phrase, or image you associate with it.</p>",
        note: "Say: Let's zoom out and look at the Depth and Complexity framework. As a group, select your word and brainstorm.",
        activityType: "text-submit",
        activityTitle: "⚡ Energizer Word Storm",
        activityPrompt: "Type your group's words, phrases, or associations for Depth or Complexity:"
      },
      {
        title: "Depth and Complexity Framework",
        content: "<p>The Depth & Complexity Framework encourages students to think critically. It also differentiates and deepens student understanding of content.</p>",
        note: "Say: Here is how we define depth and complexity within the depth and complexity framework.",
        activityType: null
      },
      {
        title: "Carnegie Problem Types & Strategy: TPR",
        content: "<p>Carnegie lessons include a variety of problem types aimed at providing depth and complexity.</p><p><strong>Strategy: Total Physical Response (TPR)</strong> - Gestures and movement to reinforce understanding.</p>",
        note: "Say: Show me your hand gesture for depth. Show me complexity. Wait to show your gesture when I say '3, 2, 1... show me'.",
        activityType: "gesture",
        activityTitle: "✋ Physical Gesture Practice",
        activityPrompt: "Ready your physical gesture, then log your selection:"
      },
      {
        title: "Problem Type: Worked Example",
        content: "<p><strong>Problem Type: Worked Example</strong></p><p>Worked examples aim at students making connections between steps.</p><ul><li><strong>Depth:</strong> Exploration of content that goes beyond facts and concepts</li><li><strong>Complexity:</strong> Extension of content by examining relationships</li></ul>",
        note: "Say: Based on our definitions, which best fits the aim of worked examples? Three, two, one... show me.",
        activityType: "gesture",
        activityTitle: "📊 Vote: Worked Examples",
        activityPrompt: "Does Worked Example align with Depth or Complexity?"
      },
      {
        title: "Problem Type: Thumbs Up/Down",
        content: "<p><strong>Problem Type: Thumbs Up/Down</strong></p><p>Requires students to look for errors and make connections between steps.</p>",
        note: "Say: Based on our definitions, which best fits the aim of thumbs up/down problems? Three, two, one... show me.",
        activityType: "gesture",
        activityTitle: "📊 Vote: Thumbs Up/Down",
        activityPrompt: "Does Thumbs Up/Down align with Depth or Complexity?"
      },
      {
        title: "Problem Type: Who's Correct?",
        content: "<p><strong>Problem Type: Who's Correct?</strong></p><p>Requires students to question the strategy by determining if reasoning makes sense and identifying errors.</p>",
        note: "Say: Based on our definitions, which best fits who's correct problems? Three, two, one... show me.",
        activityType: "gesture",
        activityTitle: "📊 Vote: Who's Correct?",
        activityPrompt: "Does Who's Correct align with Depth or Complexity?"
      },
      {
        title: "Problem Type: Thought Bubbles",
        content: "<p><strong>Problem Type: Thought Bubbles</strong></p><p>Provided to remind students about previously learned ideas, suggest strategies, share fun facts, or guide learning.</p>",
        note: "Say: Based on our definitions, which best fits thought bubbles? Three, two, one... show me.",
        activityType: "gesture",
        activityTitle: "📊 Vote: Thought Bubbles",
        activityPrompt: "Does Thought Bubbles align with Depth or Complexity?"
      },
      {
        title: "Gifted Guild Overview",
        content: "<p><em>\"The Depth and Complexity Framework is a set of tools that allow teachers to differentiate, for any grade level or content area, in a way that is straightforward to implement and effective.\"</em></p><p>— Gifted Guild's Guide to Depth and Complexity</p>",
        note: "Say: You don't have to recreate lessons. You simply use prompts to help students think more deeply.",
        activityType: null
      },
      {
        title: "Depth & Complexity Icons",
        content: "<p>Introduction to the visual prompts of the framework.</p>",
        note: "Overview slide.",
        activityType: null
      },
      {
        title: "The Toolkit of Icons",
        content: "<p>Eleven Depth and Complexity icons prompt students to delve deeper into the area of study and their thinking process.</p>",
        note: "Say: Think of the framework as a versatile toolkit designed to elevate student thinking.",
        activityType: null
      },
      {
        title: "Today's 4 Target Icons",
        content: "<ul><li><strong>Patterns:</strong> Encourages students to look for repetition</li><li><strong>Rules:</strong> Encourages students to look for organizational elements and structure</li><li><strong>Language of the Discipline:</strong> Encourages students to use content vocabulary</li><li><strong>Across Disciplines:</strong> Encourages students to make connections among many subjects</li></ul>",
        note: "Say: For our purposes today, we will focus on these 4 icons.",
        activityType: null
      },
      {
        title: "CBLI Strategy: Four Finger Scale",
        content: "<p>Look at the example problem from the curriculum and determine which Depth and Complexity icon applies using the 4-finger scale.</p>",
        note: "Say: Show me patterns, show me rules, show me language, show me across disciplines.",
        activityType: "scale",
        activityTitle: "🖐️ Four-Finger Icon Scale",
        activityPrompt: "Which of the 4 icons applies to the upcoming examples?"
      },
      {
        title: "Icon Check 1: Patterns",
        content: "<p>Look at the curriculum problem on screen. Which icon applies?</p><p><em>Question Prompt: What pattern(s) can be revealed from this problem?</em></p>",
        note: "Say: Three, two, one... show me.",
        activityType: "scale",
        activityTitle: "🔍 Icon Analysis 1",
        activityPrompt: "Select the icon that best applies:"
      },
      {
        title: "Icon Check 2: Rules",
        content: "<p>Look at the curriculum problem on screen. Which icon applies?</p><p><em>Question Prompt: What rule(s) can be established by reviewing the two responses?</em></p>",
        note: "Say: Three, two, one... show me.",
        activityType: "scale",
        activityTitle: "🔍 Icon Analysis 2",
        activityPrompt: "Select the icon that best applies:"
      },
      {
        title: "Icon Check 3: Language of Discipline",
        content: "<p>Look at the curriculum problem on screen. Which icon applies?</p><p><em>Question Prompt: How does this help students make connections?</em></p>",
        note: "Say: Three, two, one... show me.",
        activityType: "scale",
        activityTitle: "🔍 Icon Analysis 3",
        activityPrompt: "Select the icon that best applies:"
      },
      {
        title: "Icon Check 4: Across Disciplines",
        content: "<p>Look at the curriculum problem on screen. Which icon applies?</p><p><em>Question Prompt: Notice how each icon has an accompanying question prompt!</em></p>",
        note: "Say: Three, two, one... show me.",
        activityType: "scale",
        activityTitle: "🔍 Icon Analysis 4",
        activityPrompt: "Select the icon that best applies:"
      },
      {
        title: "Cross-Disciplinary Extension 1",
        content: "<p>How does this extend across disciplines? Look at the problem and determine which icon applies.</p>",
        note: "Analyze the problem stem.",
        activityType: "scale",
        activityTitle: "🌐 Disciplinary Extension",
        activityPrompt: "Select the icon:"
      },
      {
        title: "Cross-Disciplinary Extension 2",
        content: "<p>How does this extend across disciplines? Look at the problem and determine which icon applies.</p>",
        note: "Analyze the problem stem.",
        activityType: "scale",
        activityTitle: "🌐 Disciplinary Extension",
        activityPrompt: "Select the icon:"
      },
      {
        title: "Cross-Disciplinary Extension 3",
        content: "<p>How does this extend across disciplines? Look at the problem and determine which icon applies.</p>",
        note: "Analyze the problem stem.",
        activityType: "scale",
        activityTitle: "🌐 Disciplinary Extension",
        activityPrompt: "Select the icon:"
      },
      {
        title: "Model Lesson Reflection: Turn & Talk",
        content: "<p>Discuss with your neighbor any areas of opportunity within the model lesson where Depth & Complexity icons could be used.</p>",
        note: "Say: Turn and talk with your partner.",
        activityType: "text-submit",
        activityTitle: "💬 Turn & Talk Notes",
        activityPrompt: "Record 1-2 opportunities you and your partner identified:"
      },
      {
        title: "DOs and DON'Ts of Implementation",
        content: "<p><strong>DO:</strong> Introduce gradually, start with familiar topics, emphasize thinking, allow voice & choice, combine icons, make them tangible.</p><p><strong>DON'T:</strong> Ignore the 'why', use only for gifted learners, rely solely on them, forget vocabulary, use overly complicated content at first.</p>",
        note: "Say: Keep these guidelines in mind as you plan.",
        activityType: "dos-game",
        activityTitle: "🎯 Quick Check: DOs vs DON'Ts",
        activityPrompt: "Categorize the practice below:"
      },
      {
        title: "Carnegie Exploration: Make Your Mark",
        content: "<p>Scan the Carnegie lesson. Using your assigned icon number (top badge), find and mark all sections within the lesson that have opportunities to explore your icon.</p>",
        note: "Say: Recall your assigned number from your badge. Be prepared to share findings with your team.",
        activityType: "text-submit",
        activityTitle: "📌 Make Your Mark Findings",
        activityPrompt: "List the page number and task where your assigned icon appears:"
      },
      {
        title: "Benefits of Depth and Complexity Icons",
        content: "<ul><li>Encourages learners to generate ideas</li><li>Guides learners to search for deep answers at sophisticated levels</li><li>Fosters independence where students direct learning</li><li>Approaches topics the way an expert in the field would</li><li>Steers students toward meaningful information</li></ul>",
        note: "Say: Summarizing the core impacts on student learning.",
        activityType: null
      },
      {
        title: "Depth and Complexity Reflection: 4 Corners",
        content: "<p>Select the phrase that best represents your view on incorporating depth and complexity icons into your instruction:</p><ol><li>I already provide opportunities to do this</li><li>I can easily include opportunities to do this</li><li>This will take some planning</li><li>I am not sure how to provide this…yet</li></ol>",
        note: "Say: Move to the corner representing your view, then pair up for discussions!",
        activityType: "four-corners",
        activityTitle: "🚶 4 Corners Alignment",
        activityPrompt: "Select your corner to reveal your discussion partner matchup:"
      }
    ];

    let currentSlide = 0;

    // Random Icon Assignment for Participant (Badge)
    const icons = ["1: Patterns", "2: Rules", "3: Language of Discipline", "4: Across Disciplines"];
    const assigned = icons[Math.floor(Math.random() * icons.length)];
    document.getElementById('assigned-badge').innerText = `Assigned Icon: #${assigned}`;

    function renderSlide() {
      const slide = deck[currentSlide];
      document.getElementById('slide-title').innerText = slide.title;
      document.getElementById('slide-progress').innerText = `Slide ${currentSlide + 1} of ${deck.length}`;
      document.getElementById('slide-content').innerHTML = slide.content;
      document.getElementById('slide-note').innerHTML = `<strong>Presenter Note:</strong> ${slide.note}`;

      const actBox = document.getElementById('activity-box');
      
      if (slide.activityType) {
        actBox.style.display = 'block';
        actBox.innerHTML = `<h3>${slide.activityTitle}</h3><p>${slide.activityPrompt}</p>`;

        if (slide.activityType === 'text-submit') {
          actBox.innerHTML += `
            <textarea placeholder="Type your response here..."></textarea>
            <button class="act-btn" style="margin-top:10px; width:100%;" onclick="alert('Response submitted to session log!')">Submit Response</button>
          `;
        } else if (slide.activityType === 'gesture') {
          actBox.innerHTML += `
            <div class="btn-group">
              <button class="act-btn" onclick="highlightBtn(this)">Ⓓ Depth</button>
              <button class="act-btn" onclick="highlightBtn(this)">Ⓒ Complexity</button>
            </div>
          `;
        } else if (slide.activityType === 'scale') {
          actBox.innerHTML += `
            <div class="scale-grid">
              <button class="scale-btn" onclick="highlightScale(this)"><strong>⓵ Patterns</strong><br><small>Repetition</small></button>
              <button class="scale-btn" onclick="highlightScale(this)"><strong>⓶ Rules</strong><br><small>Structure</small></button>
              <button class="scale-btn" onclick="highlightScale(this)"><strong>⓷ Language</strong><br><small>Vocabulary</small></button>
              <button class="scale-btn" onclick="highlightScale(this)"><strong>⓸ Across Disciplines</strong><br><small>Connections</small></button>
            </div>
          `;
        } else if (slide.activityType === 'dos-game') {
          actBox.innerHTML += `
            <p><strong>Practice:</strong> "Using icons only for gifted learners"</p>
            <div class="btn-group">
              <button class="act-btn" onclick="alert('Correct! Icons are for ALL learners.')">DO</button>
              <button class="act-btn" onclick="alert('Correct! This is a DON\'T.')">DON'T</button>
            </div>
          `;
        } else if (slide.activityType === 'four-corners') {
          actBox.innerHTML += `
            <div class="corners-grid">
              <div class="corner-card" onclick="selectCorner(1, 'Group 1 combines with Group 4')"><strong>① Already doing this</strong></div>
              <div class="corner-card" onclick="selectCorner(2, 'Group 2 combines with Group 3')"><strong>② Can easily include</strong></div>
              <div class="corner-card" onclick="selectCorner(3, 'Group 2 combines with Group 3')"><strong>③ Takes planning</strong></div>
              <div class="corner-card" onclick="selectCorner(4, 'Group 1 combines with Group 4')"><strong>④ Not sure yet</strong></div>
            </div>
            <div id="match-result" style="margin-top:10px; font-weight:bold; color:var(--primary);"></div>
          `;
        }
      } else {
        actBox.style.display = 'none';
      }

      document.getElementById('prev-btn').disabled = currentSlide === 0;
      document.getElementById('next-btn').disabled = currentSlide === deck.length - 1;
    }

    function navigateSlide(dir) {
      currentSlide += dir;
      renderSlide();
      window.scrollTo(0, 0);
    }

    function highlightBtn(btn) {
      btn.parentElement.querySelectorAll('.act-btn').forEach(b => b.classList.remove('selected'));
      btn.classList.add('selected');
    }

    function highlightScale(btn) {
      btn.parentElement.querySelectorAll('.scale-btn').forEach(b => b.classList.remove('selected'));
      btn.classList.add('selected');
    }

    function selectCorner(num, pairing) {
      document.querySelectorAll('.corner-card').forEach(c => c.classList.remove('selected'));
      event.currentTarget.classList.add('selected');
      document.getElementById('match-result').innerText = `Corner ${num} selected! Partner Phase Matchup: ${pairing}`;
    }

    // Initialize slide deck
    renderSlide();
  </script>
</body>
</html>
