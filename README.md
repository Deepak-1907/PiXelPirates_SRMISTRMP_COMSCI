
# 🚀 InsightAI
### AI Tutor That Explains Concepts the Way Students Think

InsightAI is an AI-powered learning assistant designed for **NCERT Class 9–12 students**.

Unlike traditional AI tutors that respond in formal textbook language, InsightAI understands **codemixed student language such as Hinglish or Tanglish** and explains concepts conversationally like a helpful senior student.

The goal is to make **concept learning intuitive, interactive, and personalized**.

---

# 📚 Problem

Over **250 million students in India** study using the NCERT curriculum.

However most AI tools:

- respond in **formal academic English**
- give **long textbook explanations**
- lack **interactive learning features**

Students often ask doubts like:

Student Question Example:

bhaiya inertia kya hota hai

But typical AI responses feel like a **Wikipedia article instead of a human explanation**.

This creates a **language gap between AI tutors and real student thinking patterns**.

---

# 💡 Solution

InsightAI bridges this gap by creating a **student-friendly AI tutor** that:

- understands **codemixed language**
- explains concepts with **real-life examples**
- generates **practice questions**
- detects **student confusion**
- suggests **next learning topics**

The system behaves like a **smart senior student mentor rather than a textbook bot**.

---

# ✨ Key Features

## 🧠 Conversational AI Tutor

- Understands **Hinglish / Tanglish style questions**
- Explains concepts using **simple conversational language**
- Uses relatable examples like buses, cricket, cooking, etc.

Example interaction:

Student: bhaiya inertia kya hota hai

InsightAI responds with a simple explanation and analogy.

---

## 🔊 Voice Explanation

Students can **listen to explanations instead of reading**.

Features:

- "Listen Explanation" button
- Uses browser **SpeechSynthesis API**
- Indian English voice support

---

## 🎤 Voice Question Input

Students can **ask doubts using voice**.

Process:

1. Click microphone button
2. Speak question
3. Speech converted to text
4. Automatically sent to chatbot

Uses **Web Speech API**.

---

## 🧩 Concept Map Generator

After every explanation, InsightAI generates a **concept map**.

Example:

Photosynthesis  
→ Chlorophyll  
→ Sunlight Energy  
→ Glucose Formation  

This helps students understand **how concepts connect**.

---

## 📝 Smart Practice Questions

InsightAI automatically generates **3 difficulty levels**:

- Easy → definition recall
- Medium → application question
- Hard → conceptual reasoning

This makes the chatbot function like a **mini practice tutor**.

---

## 🔍 Confusion Detection

The system tracks **repeated student questions**.

If the same topic appears multiple times:

InsightAI automatically switches to **simpler explanations with analogies**.

Example response:

"It looks like this topic might still be confusing. Let me explain it in a simpler way."

---

## 📊 Weakness Analyzer

InsightAI identifies **topics where students struggle**.

When repeated questions occur, it generates a **mini practice test**:

Mini Test

Q1 Easy  
Q2 Medium  
Q3 Hard  

This creates **adaptive learning**.

---

## 🧭 Concept Journey (Learning Path)

After explaining a topic, InsightAI suggests **next concepts to learn**.

Example:

Learning Path

To fully understand Newton's Laws:

1. Force  
2. Momentum  
3. Friction  

This transforms the chatbot into a **guided learning system**.

---

# 🏗 Architecture

Student Question  
↓  
Frontend Chat Interface  
↓  
Backend (Node.js + Express)  
↓  
OpenAI API  
↓  
AI Response Processing  
↓  
InsightAI Structured Output

Explanation  
Concept Map  
Practice Questions  
Learning Path  

---

# ⚙ Tech Stack

Frontend:

- HTML
- CSS
- JavaScript

Backend:

- Node.js
- Express.js

AI:

- OpenAI API

Browser APIs:

- Web Speech API (Voice Input)
- SpeechSynthesis API (Voice Output)

---

# 📂 Project Structure

InsightAI  
│  
├── server.js  
├── package.json  

├── public  
│   ├── index.html  
│   ├── script.js  
│   └── style.css  

└── README.md  

---

# 🚀 Running the Project

### Clone Repository

```bash
git clone https://github.com/yourusername/InsightAI.git
```

### Install Dependencies

```bash
npm install
```

### Add API Key

Create a `.env` file:

```
OPENAI_API_KEY=your_api_key
```

### Start Server

```bash
node server.js
```

Open in browser:

```
http://localhost:3000
```

---

# 🌍 Live Demo

Example deployment:

```
https://insight-ai--yourusername.replit.app
```

---

# 🎯 Future Improvements

- diagram generation for physics concepts  
- teacher analytics dashboard  
- personalized revision plans  
- exam preparation mode  
- multilingual explanations  

---

# 👨‍💻 Author

Deepak Narayanan

B.Tech Computer Science student interested in:

- Artificial Intelligence
- EdTech
- Full-Stack Development
- AI-powered learning systems

---

# ⭐ Inspiration

InsightAI is inspired by the idea that **AI should speak the language students actually think in**.

The mission is to make **quality learning assistance accessible to millions of students**.
