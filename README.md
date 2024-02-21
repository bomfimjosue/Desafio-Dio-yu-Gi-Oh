<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <title>Yu-Gi-Oh Jo-Ken-Po</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>         <!-- ...restante do HTML... -->
<div id="mao-jogador">Mão do Jogador: </div>
<div id="mao-computador">Mão do Computador: </div>
<div id="resultado">Resultado da rodada: </div>
<!-- ...restante do HTML... -->

  <div id="jogo">
  <div id="pontos-jogador">Pontos do Jogador: <span id="pontuacao-jogador">0</span></div>
  <div id="pontos-computador">Pontos do Computador: <span id="pontuacao-computador">0</span></div>
  <!-- ... -->
</div>

    <button id="jogar-btn">Jogar</button>
  </div>
  <script src="app.js"></script>
</body>
</html>
#jogo {
  text-align: center;
}

#pontos-jogador, #pontos-computador {
  margin: 10px;
}

button {
  padding: 10px;
  margin-top: 20px;
}
// Estados do jogo
let estadoJogador = {
  pontos: 0,
  maoAtual: null
};

let estadoComputador = {
  pontos: 0,
  maoAtual: null
};
// Exporta os estados para serem usados em outros arquivos
export { estadoJogador, estadoComputador };
// Mecânica do Jo-Ken-Po
const JOGADAS = {
  PEDRA: 'pedra',
  PAPEL: 'papel',
  TESOURA: 'tesoura'
};
// Exporta as jogadas para serem usadas em outros arquivos
export { JOGADAS };
// Função para escolher uma jogada aleatória
function escolherJogada() {
  const jogadas = Object.values(JOGADAS);
  return jogadas[Math.floor(Math.random() * jogadas.length)];
}
// Importações
import { JOGADAS } from './jogadas.js';
import { estadoJogador, estadoComputador } from './estado.js';

// Função para escolher uma jogada aleatória
function escolherJogada() {
  const jogadas = Object.values(JOGADAS);
  return jogadas[Math.floor(Math.random() * jogadas.length)];
}

// Função para determinar o vencedor
function determinarVencedor(jogadaJogador, jogadaComputador) {
  // ...código existente...
}

// Função para atualizar o estado do jogo
function jogar() {
  estadoJogador.maoAtual = escolherJogada();
  estadoComputador.maoAtual = escolherJogada();
  let resultado = determinarVencedor(estadoJogador.maoAtual, estadoComputador.maoAtual);
  atualizarInterface(resultado);
  console.log(resultado); // Para depuração
}

// Função para atualizar a interface
function atualizarInterface(resultado) {
  document.getElementById('pontuacao-jogador').textContent = estadoJogador.pontos;
  document.getElementById('pontuacao-computador').textContent = estadoComputador.pontos;
  // Adicione elementos para mostrar as mãos atuais
  document.getElementById('mao-jogador').textContent = `Mão do Jogador: ${estadoJogador.maoAtual}`;
  document.getElementById('mao-computador').textContent = `Mão do Computador: ${estadoComputador.maoAtual}`;
  // Exibir o resultado da rodada
  document.getElementById('resultado').textContent = `Resultado da rodada: ${resultado}`;
}

// Event listener para o botão jogar
document.getElementById('jogar-btn').addEventListener('click', jogar);

// Iniciar o jogo
jogar();
