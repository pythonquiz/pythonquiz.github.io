# 🐍 Python Quiz

An interactive, single-file Python quiz web application. Test your Python knowledge with 200 questions across 20 categories. It includes timed questions, randomized answers, explanations, streak tracking, sound effects and progress saved in your browser.

![Python Quiz](https://img.shields.io/badge/Python-Quiz-306998?style=for-the-badge&logo=python&logoColor=FFD43B)
![License](https://img.shields.io/badge/License-MIT-FFD43B?style=for-the-badge)
![HTML](https://img.shields.io/badge/HTML-Single%20File-e34f26?style=for-the-badge&logo=html5&logoColor=white)
![Questions](https://img.shields.io/badge/Questions-200-28a745?style=for-the-badge)

## 🚀 Live Demo

**[https://pythonquiz.github.io](https://pythonquiz.github.io)**

---

## ✨ Features

### 📚 Question Bank

- **200 Questions**: 10 questions in each of 20 categories.
- **Two Difficulty Levels**: Easy and Medium, each shown with a color-coded badge.
- **Explanations**: Every question includes a short explanation of the correct answer.
- **Randomized Answers**: Each question stores 7 options. The quiz shows 5 of them: the correct answer plus 4 random wrong ones, in shuffled order.
- **Randomized Questions**: Questions are shuffled every time a quiz starts.

### 🗂️ Categories

| | | | |
|---|---|---|---|
| Basic Syntax | Data Types | Strings | Lists |
| Dictionaries | Tuples | Control Flow | Functions |
| Modules & Imports | File Handling | Exception Handling | OOP Basics |
| List Comprehensions | Built-in Functions | String Methods | Operators |
| Iterators & Generators | Decorators | Regular Expressions | Advanced Concepts |

### 🎮 Quiz Experience

- **Multi-Category Selection**: Pick one or more categories for a custom quiz.
- **Random Mix**: Start a quiz with questions from all 20 categories.
- **Countdown Timer**: Choose 15, 30, 45 or 60 seconds per question, or no timer. A warning animation plays during the last 5 seconds.
- **Instant Feedback**: Correct and incorrect answers are highlighted with animations.
- **Sound Effects**: Short tones play for correct, incorrect and timed-out answers. They are generated with the Web Audio API, so no audio files are needed.
- **Navigation**: Move between questions with Previous and Next. Answered questions keep their state.
- **Progress Bar**: Shows how far you are through the current quiz.

### 📊 Scoring & Stats

- **Points**: 10 points for an Easy question, 20 points for a Medium question.
- **Live Stats Bar**: Shows total score, questions answered, accuracy and current streak.
- **Category Mastery**: Each category card shows the percentage of its questions you have answered correctly.
- **Results Screen**: Shows an animated score circle with correct, incorrect and skipped counts.
- **Performance Ratings**: Excellent (≥90%), Great Job (≥70%), Good Effort (≥50%) and Keep Learning (below 50%).
- **Confetti Celebration**: Plays when you score 90% or higher.

### ⌨️ Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `1`–`5` or `A`–`E` | Select an answer |
| `Enter` | Next question / Finish |
| `→` | Next question (after answering) |
| `←` | Previous question |

### 🎯 General

- **Single HTML File**: No build tools, no installation and no server required.
- **Fits the Screen on Desktop**: The layout fills the viewport without page scrolling.
- **Fully Responsive**: Works on desktop, tablet and mobile, in both portrait and landscape.
- **Dark Theme**: Uses Python's blue and yellow colors with a floating emoji background animation.
- **Persistent State**: Settings, stats, category progress and an in-progress quiz are saved to `localStorage`.
- **Settings Panel**: Slide-out panel for the timer, questions per quiz, explanations, sound and a progress reset.

---

## 📦 Getting Started

### Option 1: Direct Use

1. Open **[https://pythonquiz.github.io](https://pythonquiz.github.io)** in your browser.
2. Select one or more categories, or click **Random Mix**.
3. Click **Start Quiz**.

### Option 2: Local Use

```bash
git clone https://github.com/pythonquiz/pythonquiz.github.io.git
cd pythonquiz.github.io
```

Open `index.html` in your browser. There is no build step and no server needed.

### Option 3: Download

Download `index.html` directly and open it in any modern browser.

---

## 🏗️ Architecture

```
index.html (single file)
├── HTML Structure
│   ├── Header & Stats Bar (score, answered, accuracy, streak)
│   ├── Welcome Screen (category grid, start / random buttons)
│   ├── Quiz Screen (timer, progress, question, answers, explanation, navigation)
│   ├── Results Screen (score circle, details, retry / home)
│   ├── Settings Panel (slide-out)
│   └── Toast & Confetti Canvas
├── CSS Styles
│   ├── Dark theme with CSS variables
│   ├── Floating background animation
│   ├── Desktop viewport-fit layout (no page scroll)
│   ├── Responsive mobile & landscape layouts
│   └── Transitions & feedback animations
└── JavaScript
    ├── Question Database (20 categories × 10 questions)
    ├── Quiz Engine (shuffle, 5-of-7 answer selection, scoring)
    ├── Timer
    ├── Results & Confetti
    ├── Sound Effects (Web Audio API)
    ├── Keyboard Navigation
    └── State Management (localStorage: "pythonQuizState")
```

---

## 🔧 External Libraries

| Library | Purpose | CDN |
|---------|---------|-----|
| [Font Awesome 6.4](https://fontawesome.com/) | Icons | cdnjs |
| [Poppins](https://fonts.google.com/specimen/Poppins) | Typography | Google Fonts |

No JavaScript libraries are used. All app logic is plain vanilla JavaScript.

---

## 📖 Usage Guide

### Taking a Quiz

1. **Select categories**: Click category cards to toggle them. Selected cards are highlighted in yellow.
2. **Start**: Click **Start Quiz** for your selected categories, or **Random Mix** for all categories.
3. **Answer**: Click an option or press `1`–`5` or `A`–`E` before the timer runs out.
4. **Learn**: Read the explanation that appears after each answer.
5. **Navigate**: Use **Next** and **Previous**, or the arrow keys.
6. **Review results**: See your score breakdown, then click **Try Again** or **Home**.

> 💡 **Tip:** Medium questions are worth twice as many points as Easy ones. Keep a streak going by answering correctly in a row.

### Customizing Settings

Click the ⚙️ button in the top-right corner to:

- Set the **timer duration** (or turn the timer off).
- Choose the **number of questions** per quiz (5, 10, 15, 20 or all).
- Turn **explanations** and **sound effects** on or off.
- **Reset progress** to clear your score, stats and category mastery.

> 💡 **Tip:** Your progress is saved automatically. If you close the tab during a quiz, you can continue where you left off.

---

## ➕ Adding Questions

Questions live in the `questionDatabase` object inside `index.html`. Each question uses this format:

```javascript
{
    question: "What does len('abc') return?",
    answers: ["3", "2", "4", "'abc'", "Error", "None", "0"], // 7 options
    correct: 0,              // index of the correct answer
    difficulty: "easy",      // "easy" or "medium"
    explanation: "len() returns the number of characters in the string."
}
```

To add a new category, add a new key to `questionDatabase`. Then add an icon for it in the `categoryIcons` map inside `renderCategories()`.

---

## 🤝 Contributing

Contributions are welcome. Because this is a single-file application, contributing is simple:

1. Fork the repository.
2. Edit `index.html`.
3. Test in your browser.
4. Submit a pull request.

### Guidelines

- Keep the single-file architecture.
- Keep external dependencies minimal.
- Give every question exactly 7 answer options and an explanation.
- Check that each question's answer is correct for **Python 3**.
- Test on both desktop and mobile.
- Keep the dark theme consistent.
- Keep `localStorage` compatible with earlier versions.

---

## 📄 License

MIT
