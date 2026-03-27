const quiz = [
  {
    question: "Какой язык программирования мы используем для этого квиза?",
    options: ["Python", "JavaScript", "C++", "HTML"],
    answer: "JavaScript"
  },
  {
    question: "Что означает HTML?",
    options: ["Hyper Text Markup Language", "High Text Machine Language", "Hyperlinking Text Markup Language", "Home Tool Markup Language"],
    answer: "Hyper Text Markup Language"
  },
  {
    question: "Что делает CSS?",
    options: ["Скриптит", "Оформляет страницу", "Создает базы данных", "Управляет сервером"],
    answer: "Оформляет страницу"
  }
];

let currentQuestion = 0;
let score = 0;

function showQuestion() {
  const q = quiz[currentQuestion];
  document.getElementById("question").innerText = q.question;
  const optionsDiv = document.getElementById("options");
  optionsDiv.innerHTML = "";
  q.options.forEach(option => {
    const btn = document.createElement("button");
    btn.innerText = option;
    btn.className = "option";
    btn.onclick = () => checkAnswer(option);
    optionsDiv.appendChild(btn);
  });
}

function checkAnswer(selected) {
  if (selected === quiz[currentQuestion].answer) {
    score++;
  }
  currentQuestion++;
  if (currentQuestion < quiz.length) {
    showQuestion();
  } else {
    showResult();
  }
}

function showResult() {
  document.getElementById("question").innerText = "Квиз завершен!";
  document.getElementById("options").innerHTML = "";
  document.getElementById("result").innerText = Ваш результат: ${score} из ${quiz.length};
}

// Запуск квиза
showQuestion();
