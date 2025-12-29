<!DOCTYPE html>
<html lang="ro">
<head>
<meta charset="UTF-8">
<title>Joc Revelion – Cât de bine vă cunoașteți?</title>
<style>
body {
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #ff758c, #ff7eb3);
  color: white;
  text-align: center;
  padding: 20px;
}
.card {
  background: rgba(0,0,0,0.25);
  border-radius: 15px;
  padding: 20px;
  max-width: 700px;
  margin: auto;
}
input, button {
  padding: 10px;
  border-radius: 8px;
  border: none;
  margin: 5px;
}
button {
  background: #fff;
  color: #ff4f7b;
  font-weight: bold;
  cursor: pointer;
}
.timer {
  font-size: 24px;
  margin: 10px;
}
</style>
</head>

<body>
<h1>🎆 Joc de Revelion 🎆</h1>
<h2>Cât de bine vă cunoașteți?</h2>

<div class="card">
  <h3 id="question"></h3>
  <div class="timer" id="timer">⏱️ 20</div>

  <input id="a1" placeholder="Răspuns partener 1">
  <input id="a2" placeholder="Răspuns partener 2"><br>

  <button onclick="nextQuestion()">Următoarea întrebare</button>
  <h3 id="score"></h3>
</div>

<script>
let questions = [
"Care este mâncarea preferată a partenerului?",
"Ce îl/o face să zâmbească instant?",
"Cum îi place să petreacă o seară liberă?",
"Care este filmul preferat?",
"Care este băutura preferată?",
"Unde ar merge în vacanță?",
"Ce obicei simpatic are?",
"Ce lucru mic îl/o face fericit/ă?",
"Cum este la petreceri?",
"Ce ar face dacă ar câștiga la loto?",
"Preferă relax sau aventură?",
"Ce cadou i-ar plăcea cel mai mult?",
"Cum reacționează când e obosit?",
"Este o persoană punctuală?",
"Mănâncă dulciuri des?",
"Ar sta treaz până la miezul nopții?",
"Este mai romantic sau pragmatic?",
"Ce îl/o relaxează cel mai mult?",
"Cel mai frumos moment din anul acesta?",
"Ce își dorește pentru anul viitor?"
];

let index = 0;
let points = 0;
let time = 20;
let timer;

function startTimer(){
  time = 20;
  document.getElementById("timer").innerText = "⏱️ " + time;
  timer = setInterval(() => {
    time--;
    document.getElementById("timer").innerText = "⏱️ " + time;
    if(time === 0){
      clearInterval(timer);
    }
  },1000);
}

function nextQuestion(){
  clearInterval(timer);
  let r1 = document.getElementById("a1").value.trim().toLowerCase();
  let r2 = document.getElementById("a2").value.trim().toLowerCase();

  if(r1 && r1 === r2) points++;

  document.getElementById("score").innerText = "Scor: " + points + " puncte";
  document.getElementById("a1").value = "";
  document.getElementById("a2").value = "";

  if(index < questions.length){
    document.getElementById("question").innerText = questions[index];
    index++;
    startTimer();
  } else {
    document.getElementById("question").innerText = "🎉 Joc încheiat! 🎉";
    document.getElementById("timer").innerText = "";
  }
}

nextQuestion();
</script>
</body>
</html>
