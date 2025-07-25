  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora IMC</title>
  <style>
    /* === Estilos gerais (Glassmorphism) === */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #1e2a3a;
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
      font-size: 2rem;
      color: #fff;
      margin-bottom: 20px;
      text-shadow: 0 0 12px rgba(0, 191, 255, 0.7);
    }
    .container {
      background: rgba(255, 255, 255, 0.05);
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
      backdrop-filter: blur(8px);
      max-width: 400px;
      width: 100%;
      text-align: center;
    }
    .campo {
      text-align: left;
      margin-bottom: 15px;
    }
    .campo label {
      display: block;
      margin-bottom: 5px;
      font-weight: 500;
      color: #ddd;
    }
    .campo input {
      width: 100%;
      padding: 10px;
      border: none;
      border-radius: 8px;
      background: rgba(255, 255, 255, 0.1);
      color: #fff;
      font-size: 1rem;
      transition: 0.3s;
    }
    .campo input:focus {
      background: rgba(255, 255, 255, 0.2);
      outline: none;
    }
    button {
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 8px;
      background: linear-gradient(135deg, #00c6ff, #0072ff);
      color: #fff;
      font-size: 1.1rem;
      font-weight: bold;
      cursor: pointer;
      transition: transform 0.2s, box-shadow 0.2s;
    }
    button:hover {
      transform: scale(1.05);
      box-shadow: 0 4px 20px rgba(0, 114, 255, 0.6);
    }
    #resultado {
      margin-top: 15px;
      padding: 10px;
      border-radius: 8px;
      font-size: 1rem;
    }
    footer {
      margin-top: 20px;
      color: #ccc;
      font-size: 0.9rem;
      background: rgba(255, 255, 255, 0.1);
      padding: 5px 10px;
      border-radius: 5px;
    }
  </style>
<body>
  <div class="container">
    <h1>Calculadora de IMC</h1>
    <div class="campo">
      <label for="peso">Peso (kg):</label>
      <input type="number" id="peso" placeholder="Ex: 70" min="0" step="0.1">
    </div>
    <div class="campo">
      <label for="altura">Altura (m):</label>
      <input type="text" id="altura" placeholder="Ex: 1.75" maxlength="4">
    </div>
    <button id="calcular" type="button">Calcular</button>
    <div id="resultado"></div>
  </div>

  <footer>Created by Cristian Kuhs</footer>

  <script>
    // Altura com ponto automático
    document.getElementById("altura").addEventListener("input", function () {
      let valor = this.value.replace(".", "");
      if (valor.length === 3 && !valor.includes(".")) {
        this.value = valor[0] + "." + valor.slice(1);
      }
    });

    // Cálculo do IMC
    document.getElementById("calcular").addEventListener("click", () => {
      const peso = parseFloat(document.getElementById("peso").value);
      const altura = parseFloat(document.getElementById("altura").value);
      const resultado = document.getElementById("resultado");

      if (!peso || !altura || peso <= 0 || altura <= 0) {
        resultado.textContent = "Por favor, insira valores válidos.";
        resultado.style.background = "rgba(244, 67, 54, 0.3)";
        return;
      }

      const imc = (peso / (altura * altura)).toFixed(2);
      let classificacao = "";

      if (imc < 18.5) classificacao = "Abaixo do peso";
      else if (imc < 24.9) classificacao = "Peso normal";
      else if (imc < 29.9) classificacao = "Sobrepeso";
      else if (imc < 34.9) classificacao = "Obesidade I";
      else if (imc < 39.9) classificacao = "Obesidade II";
      else classificacao = "Obesidade III";

      resultado.textContent = `Seu IMC é ${imc} (${classificacao}).`;
      resultado.style.background = "rgba(255,255,255,0.1)";
    });
  </script>
</body>
</html>
