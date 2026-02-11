[index.html](https://github.com/user-attachments/files/25223096/index.html)
<!DOCTYPE html>
<!-- define que sera um HTML -->
<html lang="pt-br">
<head>
  <!-- permite caracteres (acentos, ç..) -->
  <meta charset="UTF-8" />

  <!-- faz o site se adaptar a celulares,pc,  vulgo responsivo-->
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <!-- titulo da aba do navegador -->
  <title>Portfólio | Página Inicial</title>

  <!-- importa o CSS do bootstrap - vulgo o estilo -->
  <link 
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" 
    rel="stylesheet" 
  />

  <!-- importa os icones do Bootstrap icons -->
  <link 
    rel="stylesheet" 
    href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css"
  >

  <!-- as cores e parte da beleza, as cores tem que ser em codigo hexadecimal -->
  <style>
    
    :root{
      --brand:#006400;
      --brand-dark:#006400;
      --ink:#0f172a;
      --muted:#64748b;
      --bg:#f6f9fb;
    }

    /* estilo da pagina */
    body{
      background:var(--bg);
      color:var(--ink);
    }

    /* navbar(pra quem n sabe o que é é o menu superior) com efeito blur */
    .navbar-blur{
      background:rgba(255,255,255,.75);
      backdrop-filter:blur(10px);
      border-bottom:1px solid rgba(15,23,42,.06);
    }

    /* ponto no titulo da pag */
    .brand-dot{
      width:10px;
      height:10px;
      background:var(--brand);
      border-radius:50%;
      display:inline-block;
      margin-left:6px;
    }

    /* botao com a cor principal do site */
    .btn-brand{
      background:var(--brand);
      border-color:var(--brand);
      color:#fff;
    }

    /* efeito hover(muda a cor quando passa o mousse) do botao */
    .btn-brand:hover{
      background:var(--brand-dark);
      border-color:var(--brand-dark);
    }

    /* texto com a cor da marca */
    .text-brand{ color:var(--brand); }

    /* espacamento da secao hero */
    .hero{
      padding:70px 0;
    }

    /* Visual para os campos tecnologias, localização, etc */
    .pill{
      border:1px solid rgba(15,23,42,.12);
      border-radius:999px;
      padding:6px 12px;
      background:#fff;
      font-size:.9rem;
      color:var(--muted);
    }

    /* Imagem principal do hero */
    .hero-photo{
      width:100%;
      min-height:340px;
      object-fit:cover;
      border-radius:24px;
      border:1px solid rgba(15,23,42,.08);
      box-shadow:0 18px 30px rgba(15,23,42,.12);
    }
    /* quadrados de estatisticas */
    .stat{
      background:#fff;
      border:1px solid rgba(15,23,42,.06);
      border-radius:16px;
      padding:16px;
      text-align:center;
    }

    .stat .num{
      font-weight:800;
      font-size:1.4rem;
    }

    .stat .lbl{
      color:var(--muted);
      font-size:.9rem;
    }

    /* Espacamento padrao entre secoes */
    .section{
      padding:60px 0;
    }

    /* Card com visual suave, vulgo soft */
    .soft-card{
      background:#fff;
      border-radius:18px;
      border:1px solid rgba(15,23,42,.06);
      padding:24px;
      box-shadow:0 10px 22px rgba(15,23,42,.06);
    }

    /* Rodape */
    footer{
      border-top:1px solid rgba(15,23,42,.06);
      padding:22px 0;
      color:var(--muted);
      background:rgba(255,255,255,.7);
      backdrop-filter:blur(6px);
    }
  </style>
h</ead>

<body>

<!-- Elemento principal controlado pelo vue -->
 <!--  area que sera controlada pelo vue-->
<div id="app"> 

  <!-- NAVBAR (pra quem n sabe o que é é o menu superior) -->
  <nav class="navbar navbar-expand-lg navbar-blur sticky-top">
    <div class="container">

      <!-- Nome do perfil vindo do Vue -->
      <a class="navbar-brand fw-bold" href="#">
        {{ profile.nome }}<span class="brand-dot"></span>
      </a>

      <!-- Botao do menu mobile e tablet -->
      <button class="navbar-toggler" data-bs-toggle="collapse" data-bs-target="#menu">
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- Links do menu -->
      <div class="collapse navbar-collapse" id="menu">
        <ul class="navbar-nav ms-auto gap-lg-3">
          <li class="nav-item"><a class="nav-link" href="#sobre">Sobre</a></li>
          <li class="nav-item"><a class="nav-link" href="#portfolio">Portfólio</a></li>
          <li class="nav-item"><a class="nav-link" href="#contato">Contato</a></li>
        </ul>
      </div>

    </div>
  </nav>

  <!-- HERO (apresentação principal) -->
  <section class="hero">
    <div class="container">
      <div class="row align-items-center g-4">

        <!-- Texto -->
        <div class="col-lg-6">

          <!-- Localização e disponibilidade -->
          <div class="d-flex gap-2 mb-3">
            <span class="pill">📍 {{ profile.local }}</span>
            <span class="pill">Disponível para {{ profile.disponibilidade }}</span>
          </div>

          <!-- Nome -->
          <h1 class="display-5 fw-bold">
            Olá, eu sou <span class="text-brand">{{ profile.nome }}</span>
          </h1>

          <!-- Título profissional -->
          <p class="lead text-secondary mb-4">
            {{ profile.titulo }}
          </p>

          <!-- Lista de tecnologias (v-for) -->
          <div class="d-flex flex-wrap gap-2 mb-4">
            <span 
              v-for="t in profile.tecnologias" 
              :key="t" 
              class="pill"
            >
              {{ t }}
            </span>
          </div>

          <!--BOTAO VER PROJETOS E CONTATO -->
          <div class="d-flex flex-wrap gap-2 mb-4">
            <a href="#portfolio" class="btn btn-brand btn-lg">Ver projetos</a>
            <a href="#contato" class="btn btn-outline-dark btn-lg">Contato</a>
          </div>

          <!-- Estatísticas -->
          <div class="row g-3">
            <div 
              class="col-6 col-md-3" 
              v-for="s in stats" 
              :key="s.label"
            >
              <div class="stat">
                <div class="num">{{ s.valor }}</div>
                <div class="lbl">{{ s.label }}</div>
              </div>
            </div>
          </div>

        </div>

        <!-- FOTO DE PERFIL GRANDE -->
        <div class="col-lg-6">
          <img
            class="hero-photo"
            :src="profile.fotoHero"
            alt="Foto de destaque"
          />
        </div>

      </div>
    </div>
  </section>

  <!-- SOBRE -->
  <section id="sobre" class="section">
    <div class="container">
      <div class="soft-card">
        <h2 class="fw-bold mb-2">Sobre mim</h2>
        <p class="text-secondary mb-0">
          {{ profile.sobre }}
        </p>
      </div>
    </div>
  </section>

  <!-- PORTFÓLIO -->
  <section id="portfolio" class="section">
    <div class="container">
      <h2 class="fw-bold mb-4">Portfólio</h2>

      <div class="row g-4">
        <div 
          class="col-md-6 col-lg-4" 
          v-for="p in projetos" 
          :key="p.titulo"
        >
          <div class="soft-card h-100">

            <!-- Imagem do projeto -->
            <img
              :src="p.thumb"
              class="w-100 mb-3 rounded-4"
              style="height:180px;object-fit:cover;"
            />

            <!-- Informações -->
            <h5 class="fw-bold">{{ p.titulo }}</h5>
            <p class="text-secondary">{{ p.descricao }}</p>

            <!-- Links -->
            <div class="d-flex gap-2">
              <a :href="p.link" target="_blank" class="btn btn-outline-dark btn-sm">
                Visitar
              </a>
              <a :href="p.github" target="_blank" class="btn btn-dark btn-sm">
                GitHub
              </a>
            </div>

          </div>
        </div>
      </div>

    </div>
  </section>

  <!-- CONTATO -->
  <section id="contato" class="section">
    <div class="container">
      <div class="soft-card">
        <h2 class="fw-bold mb-3">Contato</h2>
        <p class="text-secondary mb-1">📧 {{ profile.email }}</p>
        <p class="text-secondary mb-1">🔗 {{ profile.linkedin }}</p>
        <p class="text-secondary mb-0">💻 {{ profile.github }}</p>
      </div>
    </div>
  </section>

  <!-- RODAPe -->
  <footer>
    <div class="container text-center">
      © {{ new Date().getFullYear() }} {{ profile.nome }} — Portfólio
    </div>
  </footer>

</div>

<!-- Importa o Vue -->
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>

<!-- Importa o JavaScript do Bootstrap -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

<script>
/* Extrai a função createapp do vue, basicamente vai pegar a funcao createapp que esta dentro do Vue e guarde ela numa variavel com o mesmo nome; Vue, acorda e começa a controlar essa parte da página */
const { createApp } = Vue;

/* Cria a aplicação Vue */
createApp({
  data(){
    return {

      /* Dados do perfil PREENCHER COM OS PROPRIOS DADOS */
      profile:{
        nome:"Antônio Lussi Perardt",
        titulo:"Desenvolvimento de sistemas• Full-stack•",
        local:"Cuiabá",
        disponibilidade:"Freelance / CLT/PAGANDO BEM QUE MAL TEM",
        tecnologias:["PHP","Bootstrap","HTML","CSS","PHYTON"],
        fotoHero:"https://scontent.fcgb3-1.fna.fbcdn.net/v/t39.30808-6/265923963_1510216046016440_6812266071954748296_n.jpg?_nc_cat=100&ccb=1-7&_nc_sid=6ee11a&_nc_eui2=AeEVDgKftTUF0nE9fO2gLpt1WKxPD4Mk4ZlYrE8PgyThmQybmPNhq11fYQYtA9HuKsX6DwOc2sLrg1QALTWIRqFI&_nc_ohc=buKvtFaJCCQQ7kNvwF06daJ&_nc_oc=AdkbI3ah_wG9juNcnTaisTSaGqB6VSBp-k4wbsbwJEQCH8wKusz3Xl9t-35IOAD8Fh8&_nc_zt=23&_nc_ht=scontent.fcgb3-1.fna&_nc_gid=aa_RpbJew5dDoJ-D50HShg&oh=00_AftUkR5IQazngFJhqSV5FnbXAbQ6iDj-yhoa2lWuw99W3w&oe=6991B5F2",
        sobre:"Sou aluno e tenho total comprometimento com meu progresso e sempre busco estar aprendendo cada vez mais sobre as linguagens de programações.",
        email:"antoniolussiperardt@gmail.com",
        linkedin:"https://www.linkedin.com/in/ant%C3%B4nio-lussi-perardt/",
        github:"https://github.com/Antoniolussiperardt"
      },

      /* Estatisticas, pode alterar de acordo com suas experiencias */
      stats:[
        { valor:"1+", label:"Anos" },
        { valor:"7+", label:"Projetos" },
        { valor:"100%", label:"Dedicação" },
        { valor:"landing pages", label:"Foco" }
      ],

      /* Projetos do portfolio */
      projetos:[
        {
          titulo:"Portfólio Moderno",
          descricao:"Landing page responsiva com Vue e Bootstrap.",
          thumb:"https://www.shutterstock.com/image-illustration/programming-code-abstract-technology-background-260nw-1240395943.jpg",
          link:"#",
          github:"#"
        }
      ]
    }
  }
})
/* Monta a aplicação no elemento #app, basicamente diz Vue, vá até o HTML, encontre o elemento com id app e comece a controlar tudo que está dentro dele*/
.mount("#app");
</script>

</body>
</html>
