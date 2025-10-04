# web-carta
<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Día del novio</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@1,400&display=swap" rel="stylesheet">

<style>
  :root{
    --bg: #f6efe3;           /* fondo beige */
    --envelope: #a7c7e7;     /* sobre azul pastel */
    --card-bg: #ffffff;      /* tarjeta blanca */
    --card-border: #8bbde7;  /* azul pastel más oscuro para borde */
    --shadow: rgba(11,11,11,0.15);
    --heart-black: #000000;  /* corazón negro */
    --heart-red: #e38b8b;    /* rojo pastel */
  }

  body{
    margin:0;
    min-height:100vh;
    background: var(--bg);
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    font-family:"Playfair Display", serif;
    overflow:hidden;
  }

  h1{
    font-style:italic;
    font-weight:400;
    font-size:clamp(28px, 5vw, 44px);
    color:#2f2a28;
    margin-bottom:30px;
    text-align:center;
  }

  .center{
    position:relative;
    width:320px;
    max-width:90vw;
    height:220px;
    display:flex;
    align-items:center;
    justify-content:center;
    cursor:pointer;
  }

  .envelope{
    position:relative;
    width:260px;
    height:160px;
    background:var(--envelope);
    border-radius:10px;
    box-shadow:0 10px 30px var(--shadow);
    display:flex;
    align-items:center;
    justify-content:center;
    overflow:visible;
    transition: transform 0.2s ease;
  }
  .envelope:hover{ transform:scale(1.03); }

  .envelope::before{
    content:"";
    position:absolute;
    top:-56px;
    left:0;
    right:0;
    margin:auto;
    width:0;
    height:0;
    border-left:130px solid transparent;
    border-right:130px solid transparent;
    border-bottom:56px solid var(--envelope);
    transform-origin:50% 100%;
    transition:transform 600ms cubic-bezier(.25,.9,.2,1);
  }

  /* Tarjeta */
  .card{
    position:absolute;
    width:220px;
    height:140px;
    background:var(--card-bg);
    border:3px solid var(--card-border);
    border-radius:10px;
    top:40%;
    transform:translateY(20%);
    box-shadow:0 14px 28px rgba(0,0,0,0.12);
    padding:16px;
    box-sizing:border-box;
    text-align:center;
    opacity:0;
    transition:transform 700ms cubic-bezier(.2,.9,.25,1), opacity 350ms ease;
    z-index:2;
    overflow:hidden;
  }

  .card p{
    margin:0;
    font-size:16px;
    line-height:1.4;
    font-style:italic;
    color:#2a2624;
  }

  /* Estado abierto */
  .open .envelope::before{
    transform:rotateX(180deg) translateY(-6px);
  }
  .open .card{
    transform:translateY(-120%);
    opacity:1;
  }

  .note{
    margin-top:20px;
    font-size:13px;
    color:#6b635f;
    opacity:0.9;
    font-family:sans-serif;
  }

  /* Corazones flotantes */
  .heart{
    position:absolute;
    font-size:18px;
    opacity:0.7;
    animation: float 6s infinite ease-in-out;
  }
  @keyframes float{
    0%{ transform: translateY(0) scale(1); opacity:0.7; }
    50%{ transform: translateY(-20px) scale(1.1); opacity:1; }
    100%{ transform: translateY(0) scale(1); opacity:0.7; }
  }
</style>
</head>
<body>
  <h1>💌</h1>
  <div class="center" id="mailBox">
    <div class="envelope">
      <div class="card">
        <p>Feliz día al mejor casi novio, gracias por todo lo que has hecho, quiero poder seguir teniéndote a mi lado. Te amo 🖤</p>
      </div>
    </div>
    <!-- corazones alrededor -->
    <div class="heart" style="top:-40px; left:10px; color:var(--heart-black);">❤</div>
    <div class="heart" style="top:-60px; right:20px; color:var(--heart-red); animation-delay:1s;">❤</div>
    <div class="heart" style="bottom:-30px; left:40px; color:var(--heart-black); animation-delay:2s;">❤</div>
    <div class="heart" style="bottom:-50px; right:50px; color:var(--heart-red); animation-delay:3s;">❤</div>
    <div class="heart" style="top:30%; left:-30px; color:var(--heart-red); animation-delay:1.5s;">❤</div>
    <div class="heart" style="top:40%; right:-30px; color:var(--heart-black); animation-delay:2.5s;">❤</div>
  </div>
  <div class="note">ATT:🌻🖤💫 </div>

<script>
  const mailBox = document.getElementById('mailBox');
  let opened = false;

  mailBox.addEventListener('click', () => {
    opened = !opened;
    document.body.classList.toggle('open', opened);
  });
</script>
</body>
</html>
