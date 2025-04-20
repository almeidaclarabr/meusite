<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Gerador de Diamantes - Free Fire</title>

  <!-- Bootstrap -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" />
  <!-- Font Awesome -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet"/>
  <!-- Google Font -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet"/>
  <style>
    body {
      background-color: #0d0d0d;
      color: #f1f1f1;
      font-family: 'Poppins', sans-serif;
    }
    .container {
      max-width: 600px;
      margin: 50px auto;
    }
    .header {
      text-align: center;
      margin-bottom: 40px;
    }
    .header h1 {
      font-weight: 700;
      color: #00e6e6;
    }
    .step {
      display: none;
    }
    .step.active {
      display: block;
    }
    .btn-primary {
      background-color: #00e6e6;
      border: none;
    }
    .btn-primary:hover {
      background-color: #00cccc;
    }
    .form-control, .form-select {
      background-color: #1a1a1a;
      border: 1px solid #333;
      color: #f1f1f1;
    }
    .form-control::placeholder {
      color: #999;
    }
    .card {
      background-color: #1a1a1a;
      border: none;
    }
    .card-header h2 {
      color: #00e6e6;
    }
    .share-button {
      background-color: #25D366;
      color: #fff;
      border: none;
      padding: 12px 20px;
      margin: 10px 0;
      width: 100%;
      border-radius: 5px;
      font-weight: bold;
    }
    .countdown {
      display: flex;
      justify-content: space-around;
      margin-top: 20px;
    }
    .countdown-item {
      text-align: center;
    }
    .countdown-number {
      font-size: 2rem;
      color: #00e6e6;
    }
    .loading {
      display: none;
      text-align: center;
      margin-top: 20px;
    }
    .checkmark {
      width: 60px;
      height: 60px;
      stroke: #00e6e6;
      stroke-width: 4;
      fill: none;
      margin-bottom: 20px;
    }
    footer {
      text-align: center;
      font-size: 14px;
      margin-top: 40px;
      color: #666;
    }
  </style>
</head>
<body>

<div class="container">
  <!-- Header -->
  <div class="header">
    <h1>Gerador de Diamantes</h1>
    <p>Ganhe diamantes no Free Fire agora!</p>
  </div>

  <!-- Etapa 1 -->
  <div class="step active" id="step1">
    <div class="card p-4">
      <div class="card-header">
        <h2><i class="fas fa-user"></i> Informações</h2>
      </div>
      <div class="card-body">
        <div class="mb-3">
          <label for="user-id" class="form-label">Seu ID do Free Fire</label>
          <input type="text" id="user-id" class="form-control" placeholder="123456789">
        </div>
        <div class="mb-3">
          <label for="diamonds" class="form-label">Quantidade de Diamantes</label>
          <select id="diamonds" class="form-select">
            <option value="1.000">1.000</option>
            <option value="5.000">5.000</option>
            <option value="10.000">10.000</option>
          </select>
        </div>
        <button class="btn btn-primary w-100" onclick="goToStep(2)">Continuar</button>
      </div>
    </div>
  </div>

  <!-- Etapa 2 -->
  <div class="step" id="step2">
    <div class="card p-4">
      <div class="card-header">
        <h2><i class="fas fa-share-alt"></i> Compartilhar</h2>
      </div>
      <div class="card-body">
        <p>Compartilhe com 3 amigos no WhatsApp:</p>
        <button class="share-button" onclick="fakeShare()">Compartilhar #1</button>
        <button class="share-button" onclick="fakeShare()">Compartilhar #2</button>
        <button class="share-button" onclick="fakeShare()">Compartilhar #3</button>
        <button class="btn btn-primary w-100 mt-3" onclick="goToStep(3)">Já compartilhei</button>
      </div>
    </div>
  </div>

  <!-- Etapa 3 -->
  <div class="step" id="step3">
    <div class="card p-4 text-center">
      <svg class="checkmark" viewBox="0 0 52 52">
        <circle cx="26" cy="26" r="25"/>
        <path d="M14 27l7 7 16-17"/>
      </svg>
      <h2 class="text-success">Processando!</h2>
      <p>Os diamantes serão entregues em até 24h.</p>

      <div class="countdown">
        <div class="countdown-item">
          <span class="countdown-number" id="hours">23</span>
          <div>Horas</div>
        </div>
        <div class="countdown-item">
          <span class="countdown-number" id="minutes">59</span>
          <div>Minutos</div>
        </div>
        <div class="countdown-item">
          <span class="countdown-number" id="seconds">59</span>
          <div>Segundos</div>
        </div>
      </div>
    </div>
  </div>

  <!-- Loading -->
  <div class="loading" id="loading">
    <div class="spinner-border text-info"></div>
    <p>Processando seu pedido...</p>
  </div>

  <footer>
    &copy; 2025 Free Fire Diamond Generator
  </footer>
</div>

<script>
  function goToStep(step) {
    document.querySelectorAll('.step').forEach(el => el.classList.remove('active'));
    document.getElementById('step' + step).classList.add('active');
  }

  function fakeShare() {
    alert('Link compartilhado!');
  }

  function countdown() {
    let hours = 23, minutes = 59, seconds = 59;
    setInterval(() => {
      if (seconds > 0) seconds--;
      else {
        if (minutes > 0) {
          minutes--; seconds = 59;
        } else {
          if (hours > 0) {
            hours--; minutes = 59; seconds = 59;
          }
        }
      }
      document.getElementById('hours').textContent = String(hours).padStart(2, '0');
      document.getElementById('minutes').textContent = String(minutes).padStart(2, '0');
      document.getElementById('seconds').textContent = String(seconds).padStart(2, '0');
    }, 1000);
  }

  // Iniciar contagem quando chegar à etapa 3
  document.getElementById('step3').addEventListener('transitionstart', countdown);
</script>

</body>
</html>
