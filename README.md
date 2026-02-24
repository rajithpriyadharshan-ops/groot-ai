<!DOCTYPE html>
<html>
<head>
<title>Groot AI</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>

body{
font-family: Arial;
background:#f5f5f5;
text-align:center;
}

#chatbox{
width:90%;
max-width:500px;
margin:auto;
background:white;
padding:20px;
border-radius:10px;
box-shadow:0px 0px 10px gray;
margin-top:40px;
}

input{
width:80%;
padding:10px;
font-size:16px;
}

button{
padding:10px;
font-size:16px;
background:green;
color:white;
border:none;
border-radius:5px;
}

#response{
margin-top:20px;
text-align:left;
}

</style>

</head>

<body>

<h1>Groot AI</h1>

<div id="chatbox">

<input id="userInput" placeholder="Ask Groot AI..." />

<button onclick="askAI()">Send</button>

<div id="response"></div>

</div>

<script>

async function askAI(){

let question =
document.getElementById("userInput").value;

document.getElementById("response").innerHTML =
"Thinking...";

let res = await fetch(
"https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key=AIzaSyBe3XBJybuso9iTl7Cw-Zgl18q9A3axAKA",
{
method:"POST",
headers:{
"Content-Type":"application/json"
},
body:JSON.stringify({
contents:[
{
parts:[
{ text: question }
]
}
]
})
}
);

let data = await res.json();

let answer =
data.candidates[0].content.parts[0].text;

document.getElementById("response").innerHTML =
answer;

}

</script>

</body>

</html>
