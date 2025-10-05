<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>IPTV Cinemateca Brasil</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
<style>
  body {font-family: 'Roboto', sans-serif; margin:0; padding:0; background:#1a1a1a; color:#fff;}
  header {background:#111827; padding:1.5rem; text-align:center;}
  header h1 {margin:0; font-size:2rem;}
  header p {margin-top:0.5rem; font-size:1rem; color:#ccc;}
  nav {display:flex; justify-content:center; gap:1rem; flex-wrap:wrap; margin:1rem 0;}
  nav button {background:#25D366; color:#fff; padding:0.6rem 1.2rem; border:none; border-radius:8px; cursor:pointer; font-weight:700;}
  nav button:hover {background:#128c7e;}
  .container {display:grid; grid-template-columns:repeat(auto-fill,minmax(220px,1fr)); gap:1rem; padding:1rem;}
  .card {background:#222; border-radius:12px; overflow:hidden; box-shadow:0 6px 18px rgba(0,0,0,0.3); text-align:center; transition:transform 0.3s;}
  .card:hover {transform:scale(1.05);}
  .card img {width:100%; height:320px; object-fit:cover;}
  .card h3 {margin:0.5rem 0; font-size:1rem;}
  .btn {margin:0.5rem 0; display:inline-block; padding:0.5rem 1rem; border:none; border-radius:8px; background:#25D366; color:#fff; font-weight:700; cursor:pointer; text-decoration:none; transition:background 0.3s;}
  .btn:hover {background:#128c7e;}
  .btn.secondary {background:#ff5722;}
  #qrArea {display:none; flex-direction:column; align-items:center; gap:0.5rem; margin:1rem; padding:1rem; background:#333; border-radius:10px; box-shadow:0 6px 18px rgba(0,0,0,0.5);}
  #qrArea img {border:2px solid #555; border-radius:12px;}
  footer {text-align:center; padding:2rem 1rem; color:#aaa; font-size:0.9rem; background:#111827;}
  @media(max-width:720px){.card img{height:200px;}}
</style>
</head>
<body>

<header>
  <h1>IPTV Cinemateca Brasil</h1>
  <p>Assista filmes e séries em alta qualidade, escolha seu plano e confirme via WhatsApp.</p>
</header>

<nav>
  <button onclick="solicitarTeste()">Solicitar Teste Gratuito</button>
</nav>

<div class="container" id="filmesContainer">
  <!-- Cards de filmes, imagens reais do site Cinemateca podem ser substituídas -->
  <div class="card">
    <img src="https://www.cinemateca.com.br/images/filme1.jpg" alt="Filme 1">
    <h3>Filme 1</h3>
    <button class="btn" onclick="gerarPix('Básico - 2 Telas','19.99')">Assinar R$19,99</button>
  </div>
  <div class="card">
    <img src="https://www.cinemateca.com.br/images/filme2.jpg" alt="Filme 2">
    <h3>Filme 2</h3>
    <button class="btn" onclick="gerarPix('Básico - 3 Telas','39.99')">Assinar R$39,99</button>
  </div>
  <div class="card">
    <img src="https://www.cinemateca.com.br/images/filme3.jpg" alt="Filme 3">
    <h3>Filme 3</h3>
    <button class="btn" onclick="gerarPix('Trimestral - 2 Telas','49.99')">Assinar R$49,99</button>
  </div>
  <div class="card">
    <img src="https://www.cinemateca.com.br/images/filme4.jpg" alt="Filme 4">
    <h3>Filme 4</h3>
    <button class="btn" onclick="gerarPix('Semestral - 2 Telas','99.99')">Assinar R$99,99</button>
  </div>
  <div class="card">
    <img src="https://www.cinemateca.com.br/images/filme5.jpg" alt="Filme 5">
    <h3>Filme 5</h3>
    <button class="btn" onclick="gerarPix('Anual - 3 Telas','230.00')">Assinar R$230,00</button>
  </div>
</div>

<div id="qrArea">
  <div id="qrTitle" style="font-weight:700; font-size:1.1rem;"></div>
  <img id="qrImage" src="" alt="QR Pix" style="width:260px; height:260px;">
  <div id="pixInfo" style="margin-top:0.5rem; color:#ccc;"></div>
  <div style="margin-top:0.5rem;">
    <button class="btn secondary" onclick="copiarChave()">Copiar Pix</button>
    <button class="btn" onclick="abrirWhatsConfirm()">Já paguei</button>
  </div>
</div>

<footer>
  &copy; 2025 IPTV Cinemateca | Atendimento via WhatsApp: +55 77 98846-8160
</footer>

<script>
const PIX_KEY = '86838893517';
const WHATSAPP_NUMBER = '5577988468160';
let currentPlan = null;
let currentAmount = null;

function solicitarTeste(){
  const url = 'https://wa.me/' + WHATSAPP_NUMBER + '?text=' + encodeURIComponent('Olá! Gostaria de solicitar um teste gratuito da IPTV Cinemateca.');
  window.open(url,'_blank');
}

function gerarPix(plan,amount){
  currentPlan = plan;
  currentAmount = amount;
  const payload = '00020126360014BR.GOV.BCB.PIX0114'+PIX_KEY+'520400005303986540'+amount+'5802BR5912IPTV Cinemateca6009Brasil62070503***6304ABCD';
  const qrUrl = 'https://chart.googleapis.com/chart?cht=qr&chs=320x320&chl=' + encodeURIComponent(payload);
  document.getElementById('qrTitle').innerText = plan + ' — R$' + amount;
  document.getElementById('qrImage').src = qrUrl;
  document.getElementById('pixInfo').innerText = 'Chave Pix: ' + PIX_KEY;
  document.getElementById('qrArea').style.display = 'flex';
}

function copiarChave(){
  navigator.clipboard.writeText(PIX_KEY).then(()=>alert('Chave Pix copiada!'));
}

function abrirWhatsConfirm(){
  if(!currentPlan||!currentAmount){alert('Gere o QR do plano primeiro.'); return;}
  const msg = 'Olá! Já realizei o Pix do plano ' + currentPlan + ' no valor de R$'+currentAmount;
  const url = 'https://wa.me/'+WHATSAPP_NUMBER+'?text='+encodeURIComponent(msg);
  window.open(url,'_blank');
}
</script>

</body>
</html>
