<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>IPTV Brasil — Pagamento via Pix</title>
<style>
  body{font-family:Arial,Helvetica,sans-serif;background:#f5f7fa;margin:0;padding:0;color:#111}
  header{background:#111827;color:#fff;padding:1.5rem;text-align:center}
  header h1{margin:0;font-size:1.4rem}
  .wrap{max-width:980px;margin:1.2rem auto;padding:0 1rem}
  .grid{display:flex;flex-wrap:wrap;gap:1rem;justify-content:center}
  .card{background:#fff;border-radius:10px;padding:1rem;width:320px;box-shadow:0 6px 18px rgba(17,24,39,0.08);text-align:center}
  .card img{width:100%;border-radius:8px;margin-bottom:0.8rem}
  .price{font-weight:600;color:#1e7d32;margin:0.5rem 0;font-size:1.25rem}
  .btn{display:inline-block;background:#25D366;color:#fff;padding:0.6rem 1rem;border-radius:8px;text-decoration:none;border:none;cursor:pointer;font-weight:600}
  .btn.secondary{background:#128c7e}
  .qrbox{display:flex;flex-direction:column;align-items:center;gap:0.6rem;padding:1rem;background:#fff;border-radius:10px;box-shadow:0 6px 18px rgba(17,24,39,0.06);margin-top:1rem}
  .small{font-size:0.85rem;color:#444}
  footer{margin:2rem 0;text-align:center;color:#666;font-size:0.9rem}
  @media(max-width:720px){.card{width:100%}}
</style>
</head>
<body>

<header>
  <h1>IPTV Brasil — Pagamento via Pix</h1>
  <div style="font-size:0.95rem;margin-top:6px">Chave Pix (CPF): <strong>86838893517</strong> — pague e confirme pelo WhatsApp</div>
</header>

<div class="wrap">

  <p class="small" style="text-align:center;margin:0.8rem 0">
    Escolha o plano. O QR Code será gerado com valor exato do plano — escaneie com o app do seu banco e conclua o Pix.
  </p>

  <div class="grid">

    <!-- Básico 2 telas R$19,99 -->
    <div class="card">
      <h3>Básico — 2 Telas</h3>
      <img src="https://images.unsplash.com/photo-1517602302552-471fe67acf66?auto=format&fit=crop&w=800&q=60" alt="Filmes e séries">
      <p class="small">Acesso em 2 telas simultâneas</p>
      <div class="price">R$ 19,99</div>
      <button class="btn" onclick="gerarPix('Básico - 2 Telas', '19.99')">Gerar QR Pix</button>
    </div>

    <!-- Básico 3 telas R$39,99 -->
    <div class="card">
      <h3>Básico — 3 Telas</h3>
      <img src="https://images.unsplash.com/photo-1598899134739-cd7c2f51e1ef?auto=format&fit=crop&w=800&q=60" alt="Filmes e séries">
      <p class="small">Acesso em 3 telas simultâneas</p>
      <div class="price">R$ 39,99</div>
      <button class="btn" onclick="gerarPix('Básico - 3 Telas', '39.99')">Gerar QR Pix</button>
    </div>

    <!-- Trimestral 2 telas R$49,99 -->
    <div class="card">
      <h3>Trimestral — 2 Telas</h3>
      <img src="https://images.unsplash.com/photo-1612634989863-d0ff67a79c27?auto=format&fit=crop&w=800&q=60" alt="Filmes e séries">
      <p class="small">Assinatura por 3 meses</p>
      <div class="price">R$ 49,99</div>
      <button class="btn" onclick="gerarPix('Trimestral - 2 Telas', '49.99')">Gerar QR Pix</button>
    </div>

    <!-- Semestral 2 telas R$99,99 -->
    <div class="card">
      <h3>Semestral — 2 Telas</h3>
      <img src="https://images.unsplash.com/photo-1502136969935-8a4b1fa93d3b?auto=format&fit=crop&w=800&q=60" alt="Filmes e séries">
      <p class="small">Assinatura por 6 meses</p>
      <div class="price">R$ 99,99</div>
      <button class="btn" onclick="gerarPix('Semestral - 2 Telas', '99.99')">Gerar QR Pix</button>
    </div>

    <!-- Anual 3 telas R$230,00 -->
    <div class="card">
      <h3>Anual — 3 Telas</h3>
      <img src="https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?auto=format&fit=crop&w=800&q=60" alt="Filmes e séries">
      <p class="small">Assinatura por 12 meses</p>
      <div class="price">R$ 230,00</div>
      <button class="btn" onclick="gerarPix('Anual - 3 Telas', '230.00')">Gerar QR Pix</button>
    </div>

  </div>

  <!-- Área do QR -->
  <div id="qrArea" class="qrbox" style="display:none">
    <div id="qrTitle" style="font-weight:600"></div>
    <img id="qrImage" src="" alt="QR Pix" style="width:260px;height:260px;border-radius:8px;border:1px solid #eee">
    <div class="small">Chave Pix (CPF): <strong id="pixKey">86838893517</strong></div>
    <div class="small">Valor: <strong id="pixAmount"></strong></div>
    <div style="margin-top:0.6rem">
      <button class="btn secondary" onclick="copiarChave()">Copiar chave</button>
      <button class="btn" onclick="abrirWhatsConfirm()">Já paguei — Confirmar no WhatsApp</button>
    </div>
    <div class="small" style="margin-top:0.6rem;color:#555">Após efetuar o Pix, clique em "Já paguei" para enviar confirmação pelo WhatsApp.</div>
  </div>

  <footer>
    <p class="small">Teste sempre com um valor pequeno antes de aceitar pagamentos em produção. Nós não processamos pagamentos — o Pix será feito pelo app do banco do cliente.</p>
  </footer>

</div>

<script>
const PIX_KEY = '86838893517';
const MERCHANT_NAME = 'IPTV Brasil';
const MERCHANT_CITY = 'BRASIL';
const PROVIDER_GUI = 'br.gov.bcb.pix';

function emvField(tag, value){
  const s = String(value);
  const len = String(s.length).padStart(2, '0');
  return tag + len + s;
}

function crc16(payload){
  const bytes = [];
  for(let i=0;i<payload.length;i++){bytes.push(payload.charCodeAt(i));}
  let crc = 0xFFFF;
  for(let offset=0; offset<bytes.length; offset++){
    crc ^= (bytes[offset] << 8);
    for(let bit=0; bit<8; bit++){
      if ((crc & 0x8000) !== 0){crc = ((crc << 1) ^ 0x1021) & 0xFFFF;} else {crc = (crc << 1) & 0xFFFF;}
    }
  }
  return crc.toString(16).toUpperCase().padStart(4,'0');
}

function gerarPayloadPix(valor, txid){
  let payload = emvField('00','01');
  const mai = emvField('00', PROVIDER_GUI) + emvField('01', PIX_KEY);
  payload += emvField('26', mai);
  payload += emvField('52','0000');
  payload += emvField('53','986');
  if(valor && String(valor).trim() !== ''){payload += emvField('54', String(valor));}
  payload += emvField('58','BR');
  let name = MERCHANT_NAME.substring(0,25);
  payload += emvField('59', name);
  let city = MERCHANT_CITY.substring(0,15);
  payload += emvField('60', city);
  const tx = txid ? emvField('05', txid) : emvField('05', '***');
  payload += emvField('62', tx);
  const payloadForCrc = payload + '6304';
  const crc = crc16(payloadForCrc);
  payload += emvField('
