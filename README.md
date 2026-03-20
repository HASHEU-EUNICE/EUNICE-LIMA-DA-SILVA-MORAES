<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<title>Mochila Virtual - 2º Técnico</title>

<style>
body {
    font-family: Arial;
    background: linear-gradient(to right, #0a3d62, #3c6382);
    color: white;
    margin: 0;
}

h1 {
    text-align: center;
    padding: 15px;
}

.area {
    margin: 20px;
}

.area h2 {
    background: #1e5f8a;
    padding: 10px;
    border-radius: 10px;
}

.container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 15px;
    margin-top: 10px;
}

.materia {
    background: #1e5f8a;
    border-radius: 15px;
    padding: 10px;
}

input {
    width: 90%;
    padding: 5px;
    border-radius: 5px;
    border: none;
    text-align: center;
}

textarea {
    width: 95%;
    height: 120px;
    margin-top: 10px;
    border-radius: 10px;
    border: none;
    padding: 10px;
}
</style>
</head>

<body>

<h1>🎒 Mochila Virtual - 2º Ano Técnico</h1>

<div id="app"></div>

<script>

const dados = {
    "📚 Base Comum": [
        "Português",
        "Matemática",
        "História",
        "Geografia",
        "Biologia",
        "Química",
        "Física",
        "Inglês",
        "Educação Física",
        "Filosofia",
        "Sociologia",
        "Projeto de Vida"
    ],

    "💻 Área Técnica (Informática)": [
        "Lógica de Programação",
        "Algoritmos",
        "Programação",
        "Desenvolvimento Web",
        "Banco de Dados",
        "Redes de Computadores",
        "Sistemas Operacionais",
        "Hardware e Manutenção",
        "Segurança da Informação",
        "Engenharia de Software",
        "UX/UI Design",
        "Projeto Técnico"
    ],

    "🧠 Complementares": [
        "Empreendedorismo",
        "Educação Financeira",
        "Comunicação e Expressão",
        "Tecnologia e Sociedade"
    ]
};

const app = document.getElementById("app");

let id = 0;

for (let area in dados) {

    let divArea = document.createElement("div");
    divArea.className = "area";

    let tituloArea = document.createElement("h2");
    tituloArea.textContent = area;

    let container = document.createElement("div");
    container.className = "container";

    dados[area].forEach(materia => {

        let box = document.createElement("div");
        box.className = "materia";

        let input = document.createElement("input");
        input.value = localStorage.getItem("titulo"+id) || materia;

        input.oninput = () => {
            localStorage.setItem("titulo"+id, input.value);
        };

        let textarea = document.createElement("textarea");
        textarea.placeholder = "Escreva suas anotações...";
        textarea.value = localStorage.getItem("texto"+id) || "";

        textarea.oninput = () => {
            localStorage.setItem("texto"+id, textarea.value);
        };

        box.appendChild(input);
        box.appendChild(textarea);
        container.appendChild(box);

        id++;
    });

    divArea.appendChild(tituloArea);
    divArea.appendChild(container);
    app.appendChild(divArea);
}

</script>

</body>
</html>
