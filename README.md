<!DOCTYPE html>
<html>
<head>
    <title>Квиз</title>
</head>
<body>

<h1>Квиз</h1>

<p id="question"></p>

<button onclick="answer(0)" id="btn0"></button>
<button onclick="answer(1)" id="btn1"></button>
<button onclick="answer(2)" id="btn2"></button>

<p id="result"></p>

<script>
let questions = [
    {
        question: "Столица Франции?",
        answers: ["Париж", "Берлин", "Рим"],
        correct: 0
    },
    {
        question: "2 + 2 = ?",
        answers: ["3", "4", "5"],
        correct: 1
    },
    {
        question: "Цвет неба?",
        answers: ["Синий", "Зелёный", "Красный"],
        correct: 0
    }
];

let current = 0;
let score = 0;

function loadQuestion() {
    document.getElementById("question").innerText = questions[current].question;

    document.getElementById("btn0").innerText = questions[current].answers[0];
    document.getElementById("btn1").innerText = questions[current].answers[1];
    document.getElementById("btn2").innerText = questions[current].answers[2];
}

function answer(i) {
    if (i === questions[current].correct) {
        score++;
        document.getElementById("result").innerText = "Правильно!";
    } else {
        document.getElementById("result").innerText = "Неправильно!";
    }

    current++;

    if (current < questions.length) {
        setTimeout(loadQuestion, 1000);
    } else {
        document.body.innerHTML = "<h1>Ты набрал " + score + " очков из " + questions.length + "</h1>";
    }
}

loadQuestion();
  
</script>

</body>
</html>
