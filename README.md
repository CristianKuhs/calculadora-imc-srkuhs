<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora IMC</title>
  <style>
    /* ==== RESET E BASE ==== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      padding: 20px;
    }
    h1 {
      text-align: center;
      margin-bottom: 20px;
      font-size: 2.2rem;
      color: #f8f8f8;
      text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
    }
    /* ==== CONTAINER ==== */
    .container {
      background: rgba(255, 255, 255, 0.05);
      border-radius: 20px;
      padding: 30px;
      width: 100%;
      max-width: 400px;
      backdrop-filter: blur(8px);
      box-shadow: 0 4px 30px rgba(0, 0, 0, 0.3);
      animation: fadeIn 1s ease forwards;
      margin-bottom: 20px;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    /* ==== INPUTS E BOTÃO ==== */
    .campo {
      display: flex;
      flex-direction: column;
      margin-bottom: 15px;
    }
    .campo label {
      margin-bottom: 5px;
      font-weight: 500;
      color: #ddd;
    }
    .campo input {
      padding: 10px;
      border-radius: 10px;
      border: none;
      outline: none;
      background: rgba(255, 255, 255, 0.1);
      color: #fff;
      font-size: 1rem;
      transition: background 0.3s;
    }
    .campo input:focus {
      background: rgba(255, 255, 255, 0.2);
    }
    button {
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 12px;
      background: linear-gradient(135deg, #00c6ff, #0072ff);
      color: #fff;
      font-size: 1rem;
      font-weight: bold;
      cursor: pointer;
      transition: transform 0.2s, box-shadow 0.2s;
    }
    button:hover {
      transform: scale(1.05);
      box-shadow: 0 4px 20px rgba(0, 114, 255, 0.5);
    }
    /* ==== RESULTADO ==== */
    #resultado {
      margin-top: 20px;
      padding: 15px;
      border-radius: 12px;
      text-align: center;
      font-size: 1.2rem;
      font-weight: 500;
      transition: background 0.3s, transform 0.3s;
    }
    .bom {
      background: rgba(0, 200, 83, 0.3);
      color: #00e676;
    }
    .alerta {
      background: rgba(255, 193, 7, 0.3);
      color: #ffca28;
    }
    .perigo {
      background: rgba(244, 67, 54, 0.3);
      color: #ff5252;
    }
    /* ==== FOOTER ==== */
    footer {
      text-align: center;
      font-size: 0.9rem;
      color: #ccc;
      margin-top: auto;
      padding: 10px;
      background: rgba(255, 255, 255, 0.05);
      border-radius: 10px;
      width: fit-content;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
      animation: fadeIn 1.5s ease;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Calculadora de IMC</h1>
    <div class="campo">
      <label for="peso">Peso (kg):</label>
      <input type="number" id="peso" placeholder="Ex: 70">
    </div>
    <div class="campo">
      <label for="altura">Altura (m):</label>
      <input type="number" id="altura" placeholder="Ex: 1.75" step="0.01">
    </div>
    <button id="calcular">Calcular</button>
    <div id="resultado"></div>
  </div>

  <footer>Created by Cristian Kuhs</footer>

  <script>
    document.getElementById("calcular").addEventListener("click", function () {
      const peso = parseFloat(document.getElementById("peso").value);
      const altura = parseFloat(document.getElementById("altura").value);
      const resultado = document.getElementById("resultado");

      if (!peso || !altura || peso <= 0 || altura <= 0) {
        resultado.textContent = "Por favor, insira valores válidos.";
        resultado.className = "perigo";
        return;
      }

      const imc = (peso / (altura * altura)).toFixed(2);
      let classificacao = "";
      let classe = "";

      if (imc < 18.5) {
        classificacao = "Abaixo do peso";
        classe = "alerta";
      } else if (imc < 24.9) {
        classificacao = "Peso normal";
        classe = "bom";
      } else if (imc < 29.9) {
        classificacao = "Sobrepeso";
        classe = "alerta";
      } else if (imc < 34.9) {
        classificacao = "Obesidade I";
        classe = "alerta";
      } else if (imc < 39.9) {
        classificacao = "Obesidade II";
        classe = "al
