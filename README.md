<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3Análise de Vetor</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        input, button {
            padding: 10px;
            margin: 5px;
        }
        .result {
            margin-top: 20px;
        }
        .container{
            align-items: center;
            align-content: center;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container"></div>
    <h1>Insira 10 números inteiros</h1>
    <input type="number" id="numInput" placeholder="Digite um número" />
    <button onclick="adicionarNumero()">Adicionar número</button>
    <h2>Números inseridos:</h2>
    <p id="numerosInseridos"></p>
    <button onclick="calcularResultados()">Calcular</button>
    <div class="result">
        <p>Números maiores que a média: <span id="maioresMedia"></span></p>
        <p>Número de elementos menores que zero: <span id="menoresZero"></span></p>
    </div>
    </div>
    <script>
        let numeros = [];
        function adicionarNumero() {
            const input = document.getElementById('numInput');
            const valor = parseInt(input.value);
            if (!isNaN(valor) && numeros.length < 10) {
                numeros.push(valor);
                document.getElementById('numerosInseridos').textContent = numeros.join(', ');
                input.value = '';
            } else if (numeros.length >= 10) {
                alert("Você já inseriu 10 números.");
            } else {
                alert("Por favor, insira um número válido.");
            }
        }
        function calcularResultados() {
            if (numeros.length < 10) {
                alert("Por favor, insira 10 números.");
                return;
            }
            const soma = numeros.reduce((acc, num) => acc + num, 0);
            const media = soma / numeros.length;
            const maioresQueMedia = numeros.filter(num => num > media);
            document.getElementById('maioresMedia').textContent = maioresQueMedia.join(', ');
            const menoresQueZero = numeros.filter(num => num < 0).length;
            document.getElementById('menoresZero').textContent = menoresQueZero;
        }
    </script>
</body>
</html>
