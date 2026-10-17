
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aprenda a Criar Games</title>
<style>
* { box-sizing: border-box; }
body {
  margin: 0; padding: 20px;
  font-family: Arial, sans-serif;
  background: #0b1020; color: white;
}
main { max-width: 850px; margin: auto; }
section {
  background: #151d35; padding: 22px;
  margin: 20px 0; border-radius: 15px;
}
h1, h2 { color: #65e6b4; }
p, li { line-height: 1.7; }
button {
  padding: 12px 18px; border: 0;
  border-radius: 8px; cursor: pointer;
  background: #65e6b4; font-weight: bold;
  margin-top: 12px;
}
button:hover { background: #a1f5d5; }
video { width: 100%; border-radius: 10px; }
#quiz { display: none; }
.pergunta {
  background: #202b49; padding: 15px;
  margin: 15px 0; border-radius: 10px;
}
label { display: block; padding: 7px; cursor: pointer; }
#resultado {
  margin-top: 15px; font-size: 20px;
  color: #65e6b4; font-weight: bold;
}
</style>
</head>
<body>
<main>
<header>
  <h1>🎮 Aprenda a Criar Games</h1>
  <p>Assista à mini-aula e responda ao quiz para testar seus conhecimentos!</p>
</header>

<section>
  <h2>1. Mini-aula: como criar games</h2>
  <video id="video" controls playsinline></video>
  <p id="aviso">Preparando a animação da aula...</p>
  <h3>O que você precisa aprender:</h3>
  <ul>
    <li><b>Planejar:</b> escolher a ideia do jogo.</li>
    <li><b>Construir:</b> criar personagens e cenários.</li>
    <li><b>Programar:</b> fazer os comandos funcionarem.</li>
    <li><b>Testar:</b> encontrar e corrigir erros.</li>
  </ul>
</section>

<section>
  <h2>Resumo</h2>
  <p>HTML organiza páginas, CSS cuida do visual e JavaScript cria ações. Unity e Godot são ferramentas usadas para desenvolver jogos. Testar o jogo ajuda a descobrir problemas.</p>
  <button onclick="document.getElementById('quiz').style.display='block';document.getElementById('quiz').scrollIntoView({behavior:'smooth'})">
    Começar o quiz →
  </button>
</section>

<section id="quiz">
  <h2>2. Quiz: você entendeu?</h2>
  <form id="form">
    <div class="pergunta">
      <p>1. Qual é o primeiro passo para criar um jogo?</p>
      <label><input type="radio" name="q1" value="a" required> Publicar imediatamente</label>
      <label><input type="radio" name="q1" value="b"> Planejar a ideia</label>
      <label><input type="radio" name="q1" value="c"> Apagar os arquivos</label>
    </div>

    <div class="pergunta">
      <p>2. Para que serve a programação?</p>
      <label><input type="radio" name="q2" value="a" required> Apenas mudar as cores</label>
      <label><input type="radio" name="q2" value="b"> Aumentar a tela</label>
      <label><input type="radio" name="q2" value="c"> Criar ações e regras</label>
    </div>

    <div class="pergunta">
      <p>3. O que pode ser usado para criar jogos no navegador?</p>
      <label><input type="radio" name="q3" value="a" required> Apenas imagens</label>
      <label><input type="radio" name="q3" value="b"> HTML, CSS e JavaScript</label>
      <label><input type="radio" name="q3" value="c"> Apenas documentos de texto</label>
    </div>

    <div class="pergunta">
      <p>4. O que fazer quando encontrar um erro?</p>
      <label><input type="radio" name="q4" value="a" required> Ignorar sempre</label>
      <label><input type="radio" name="q4" value="b"> Desistir</label>
      <label><input type="radio" name="q4" value="c"> Testar e corrigir</label>
    </div>

    <div class="pergunta">
      <p>5. O que é uma game engine, como Unity?</p>
      <label><input type="radio" name="q5" value="a" required> Um controle de videogame</label>
      <label><input type="radio" name="q5" value="b"> Um site de filmes</label>
      <label><input type="radio" name="q5" value="c"> Uma ferramenta para desenvolver jogos</label>
    </div>

    <button type="submit">Ver minha pontuação</button>
    <button type="reset">Limpar respostas</button>
  </form>
  <div id="resultado"></div>
</section>
</main>

<script>
// Mini-aula animada criada no próprio HTML.
const canvas = document.createElement('canvas');
canvas.width = 800;
canvas.height = 450;
const ctx = canvas.getContext('2d');

const cenas = [
  ['COMO CRIAR UM GAME', 'Comece com uma boa ideia!'],
  ['1. CONSTRUA O MUNDO', 'Crie cenários e personagens.'],
  ['2. PROGRAME', 'Faça o personagem se movimentar.'],
  ['3. TESTE O JOGO', 'Encontre e corrija os erros.'],
  ['4. COMPARTILHE', 'Mostre seu jogo ao mundo!']
];

function desenhar(t) {
  const i = Math.min(4, Math.floor(t / 5));
  ctx.fillStyle = '#101a35';
  ctx.fillRect(0, 0, 800, 450);

  ctx.fillStyle = '#65e6b4';
  ctx.fillRect(35, 40, 7, 65);

  ctx.fillStyle = 'white';
  ctx.font = 'bold 32px Arial';
  ctx.fillText(cenas[i][0], 60, 85);

  ctx.font = '23px Arial';
  ctx.fillStyle = '#c8d5f5';
  ctx.fillText(cenas[i][1], 60, 145);

  // Personagem e plataformas.
  ctx.fillStyle = '#354c80';
  ctx.fillRect(80, 330, 640, 20);
  ctx.fillRect(210, 275, 120, 15);
  ctx.fillRect(480, 245, 120, 15);

  const x = 120 + (t * 45) % 540;
  ctx.fillStyle = '#65e6b4';
  ctx.fillRect(x, 280, 30, 50);

  ctx.fillStyle = '#ffcc66';
  ctx.beginPath();
  ctx.arc(x + 15, 270, 15, 0, Math.PI * 2);
  ctx.fill();

  ctx.fillStyle = '#65e6b4';
  ctx.fillRect(40, 390, 720 * (t / 25), 6);
}

let gravando = [];
const video = document.getElementById('video');

async function criarVideo() {
  if (!canvas.captureStream || !window.MediaRecorder) {
    document.getElementById('aviso').textContent =
      'Seu navegador não permite gerar o vídeo automaticamente. Leia o resumo da aula abaixo.';
    return;
  }

  try {
    const stream = canvas.captureStream(20);
    const tipo = MediaRecorder.isTypeSupported('video/webm;codecs=vp9')
      ? 'video/webm;codecs=vp9' : 'video/webm';

    const gravador = new MediaRecorder(stream, { mimeType: tipo });

    gravador.ondataavailable = e => {
      if (e.data.size) gravando.push(e.data);
    };

    gravador.onstop = () => {
      video.src = URL.createObjectURL(
        new Blob(gravando, { type: 'video/webm' })
      );
      document.getElementById('aviso').textContent =
        'Mini-aula pronta! Clique em Play para assistir.';
    };

    gravador.start();
    let frame = 0;

    const intervalo = setInterval(() => {
      desenhar(frame / 20);
      frame++;

      if (frame >= 500) {
        clearInterval(intervalo);
        gravador.stop();
        stream.getTracks().forEach(track => track.stop());
      }
    }, 50);
  } catch (erro) {
    document.getElementById('aviso').textContent =
      'Não foi possível gerar o vídeo neste navegador. Use o resumo da aula.';
  }
}

desenhar(0);
criarVideo();

// Corrige as respostas e calcula a pontuação.
document.getElementById('form').addEventListener('submit', function(e) {
  e.preventDefault();

  const corretas = {
    q1: 'b',
    q2: 'c',
    q3: 'b',
    q4: 'c',
    q5: 'c'
  };

  let pontos = 0;

  for (const pergunta in corretas) {
    const resposta = this.querySelector(
      `input[name="${pergunta}"]:checked`
    );

    if (resposta && resposta.value === corretas[pergunta]) {
      pontos++;
    }
  }

  let mensagem = pontos === 5
    ? 'Excelente! Você entendeu tudo!'
    : pontos >= 3
    ? 'Muito bem! Revise o que errou e tente novamente.'
    : 'Continue estudando! Você pode tentar novamente.';

  document.getElementById('resultado').textContent =
    `Você acertou ${pontos} de 5! ${mensagem}`;
});

document.getElementById('form').addEventListener('reset', function() {
  document.getElementById('resultado').textContent = '';
});
</script>
</body>
</html>
