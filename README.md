// InsightAI Full Application
// Backend + Frontend in a single Node.js file

const express = require("express");
const cors = require("cors");
const OpenAI = require("openai");

const app = express();

app.use(cors());
app.use(express.json());

const client = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY
});

let topicHistory = {};

app.get("/", (req, res) => {

res.send(`

<!DOCTYPE html>
<html>

<head>

<title>InsightAI</title>

<style>

body{
font-family: Arial;
background:#f5f5f5;
margin:0;
padding:0;
text-align:center;
}

h1{
background:#222;
color:white;
padding:20px;
margin:0;
}

#chat{
width:70%;
margin:auto;
margin-top:20px;
background:white;
height:400px;
overflow:auto;
padding:20px;
border-radius:10px;
}

.message{
margin:10px 0;
padding:10px;
border-radius:8px;
}

.user{
background:#d1e7ff;
}

.bot{
background:#e8e8e8;
}

#inputArea{
margin-top:20px;
}

input{
width:40%;
padding:10px;
font-size:16px;
}

button{
padding:10px 15px;
font-size:16px;
margin:5px;
cursor:pointer;
}

.section{
margin-top:10px;
padding:10px;
background:#fafafa;
border-radius:8px;
}

</style>

</head>

<body>

<h1>InsightAI</h1>

<div id="chat"></div>

<div id="inputArea">

<input id="question" placeholder="Ask your doubt..." />

<button onclick="sendMessage()">Send</button>

<button onclick="startVoice()">🎤 Ask with Voice</button>

</div>

<script>

function addMessage(text, type){

const chat = document.getElementById("chat");

const div = document.createElement("div");

div.className = "message " + type;

div.innerText = text;

chat.appendChild(div);

chat.scrollTop = chat.scrollHeight;

}

async function sendMessage(){

const input = document.getElementById("question");

const message = input.value;

if(!message) return;

addMessage("You: " + message,"user");

input.value = "";

const res = await fetch("/chat",{

method:"POST",

headers:{
"Content-Type":"application/json"
},

body:JSON.stringify({
message
})

});

const data = await res.json();

addMessage("InsightAI:\\n\\n" + data.reply,"bot");

createVoiceButton(data.reply);

}

function createVoiceButton(text){

const chat = document.getElementById("chat");

const btn = document.createElement("button");

btn.innerText = "🔊 Listen Explanation";

btn.onclick = function(){

const speech = new SpeechSynthesisUtterance(text);

speech.lang = "en-IN";

speechSynthesis.speak(speech);

}

chat.appendChild(btn);

}

function startVoice(){

const recognition = new webkitSpeechRecognition();

recognition.lang = "en-IN";

recognition.start();

recognition.onresult = function(event){

const transcript = event.results[0][0].transcript;

document.getElementById("question").value = transcript;

sendMessage();

}

}

</script>

</body>

</html>

`);

});


app.post("/chat", async (req,res)=>{

const message = req.body.message;

const topic = message.toLowerCase();

if(!topicHistory[topic]){

topicHistory[topic] = 0;

}

topicHistory[topic]++;

let confusionText = "";

if(topicHistory[topic] >= 2){

confusionText =
"It seems you are asking about this topic multiple times. Let me explain it in a simpler way using a real-life example.";

}

const response = await client.chat.completions.create({

model:"gpt-4o-mini",

messages:[

{
role:"system",
content:`

You are InsightAI, an AI tutor for NCERT class 9-12 students.

Rules:

1. Understand Hinglish or Tanglish questions.
2. Explain concepts conversationally like a senior student.
3. Use simple examples (cricket, buses, cooking).
4. Stay within Physics, Chemistry, Math, Biology syllabus.

Your response structure:

Explanation

Concept Map

Practice Questions
Easy
Medium
Hard

Learning Path

`
},

{
role:"user",
content: confusionText + message
}

]

});

const reply = response.choices[0].message.content;

res.json({
reply
});

});


app.listen(3000, ()=>{

console.log("InsightAI running on port 3000");

});
