<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Formulário Interativo</title>
  <style>
    body {
      background-color: pink;
      font-family: Arial, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    .form-container {
      text-align: center;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    .question {
      margin: 20px 0;
      font-size: 18px;
    }
    button {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 16px;
      color: white;
      background-color: #007BFF;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
    .finalizado {
      font-size: 24px;
      color: green;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="form-container">
    <div id="form">
      <div class="question" id="question">Você dormiu bem?</div>
      <div>
        <button onclick="selectAnswer('Sim')">Sim</button>
        <button onclick="selectAnswer('Não')">Não</button>
      </div>
    </div>
    <div id="finalizado" class="finalizado" style="display: none;">FINALIZADO</div>
  </div>

  <script>
    const questions = [
      "Você dormiu bem?",
      "Você está bem hoje?",
      "Vamos fazer amor hoje?"
    ];
    let answers = [];
    let currentQuestion = 0;

    function selectAnswer(answer) {
      answers.push({ question: questions[currentQuestion], answer: answer });
      currentQuestion++;
      if (currentQuestion < questions.length) {
        document.getElementById("question").innerText = questions[currentQuestion];
      } else {
        showSendButton();
      }
    }

    function showSendButton() {
      const form = document.getElementById("form");
      form.innerHTML = `
        <button onclick="sendAnswers()">Enviar</button>
      `;
    }

    function sendAnswers() {
      const email = "chdsluna@gmail.com";
      const subject = "Respostas do Formulário";
      const body = answers.map(a => `${a.question}: ${a.answer}`).join("\n");
      const mailtoLink = `mailto:${email}?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;

      window.location.href = mailtoLink;
      document.getElementById("form").style.display = "none";
      document.getElementById("finalizado").style.display = "block";
    }
  </script>
</body>
</html>
# verificacao
VERIFICACAO.COM
