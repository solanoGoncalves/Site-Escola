<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Escola Neusa Barbosa</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body { font-family: 'Segoe UI', sans-serif; background: #001f3f; color: white; }

    header {
      background-color: #001933;
      padding: 20px 30px;
      display: flex;
      align-items: center;
      gap: 20px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
      z-index: 1000;
    }
    header img { width: 60px; height: 60px; border-radius: 50%; }
    .titulo-escola {
      display: flex;
      flex-direction: column;
      color: white;
      text-shadow: 2px 2px 4px black;
      line-height: 1.2;
    }
    .titulo-escola span:nth-child(1) { font-size: 18px; font-weight: bold; }
    .titulo-escola span:nth-child(2) { font-size: 24px; font-weight: bold; }
    .titulo-escola span:nth-child(3) { font-size: 24px; font-weight: bold; }

    nav {
      background-color: #002d5c;
      display: flex;
      justify-content: center;
      padding: 12px 0;
      position: sticky;
      top: 0;
      z-index: 999;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
    }
    nav ul {
      list-style: none;
      display: flex;
      gap: 20px;
      align-items: center;
      position: relative;
    }
    nav ul li {
      position: relative;
    }
    nav ul li a {
      color: white;
      text-decoration: none;
      font-weight: bold;
      padding: 8px 12px;
      display: block;
      cursor: pointer;
      transition: color 0.3s;
    }
    nav ul li a:hover,
    nav ul li a.active {
      color: gold;
    }

    nav ul li ul.submenu {
      position: absolute;
      top: 40px;
      left: 0;
      background-color: #002d5c;
      border-radius: 6px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.5);
      min-width: 200px;
      opacity: 0;
      visibility: hidden;
      transition: opacity 0.3s ease;
      z-index: 1000;
      flex-direction: column;
      padding: 10px 0;
    }
    nav ul li:hover > ul.submenu,
    nav ul li.submenu-open > ul.submenu {
      opacity: 1;
      visibility: visible;
    }
nav ul li ul.submenu li a {
  padding: 10px 20px;
  font-weight: normal;
  white-space: nowrap;
  text-align: left;
  width: 100%;
  display: block;
  font-size: 15px;
    }
    nav ul li ul.submenu li a:hover {
      background-color: gold;
      color: #001f3f;
    }

    .hamburger {
      display: none;
      flex-direction: column;
      justify-content: space-around;
      width: 28px;
      height: 24px;
      cursor: pointer;
      z-index: 1100;
    }
    .hamburger div {
      width: 100%;
      height: 3px;
      background-color: white;
      border-radius: 3px;
      transition: all 0.3s ease;
    }

    @media (max-width: 768px) {
      nav {
        justify-content: flex-start;
        padding-left: 20px;
      }
      nav ul {
        flex-direction: column;
        position: fixed;
        top: 80px;
        left: -250px;
        background-color: #001f3f;
        height: 100vh;
        width: 250px;
        padding-top: 20px;
        gap: 10px;
        transition: left 0.3s ease;
      }
      nav ul.open {
        left: 0;
      }
      nav ul li {
        width: 100%;
      }
      nav ul li ul.submenu {
        position: static;
        opacity: 1 !important;
        visibility: visible !important;
        background-color: transparent;
        box-shadow: none;
        padding-left: 20px;
      }
      nav ul li ul.submenu li a:hover {
        background-color: transparent;
        color: gold;
      }
      .hamburger {
        display: flex;
        margin-left: auto;
      }
    }

    .hamburger.open div:nth-child(1) {
      transform: rotate(45deg) translate(5px, 5px);
    }
    .hamburger.open div:nth-child(2) {
      opacity: 0;
    }
    .hamburger.open div:nth-child(3) {
      transform: rotate(-45deg) translate(5px, -5px);
    }

    .transicao-para-imagem { height: 80px; background: linear-gradient(to bottom, #001f3f, rgba(0, 20, 50, 0)); }
    .banner {
      position: relative;
      height: 80vh;
      background: url('https://paracatunews.com.br/images/noticias/39648/3de301d85b480d68e656dc34fba061f3.jpg') no-repeat center center/cover;
      margin-top: 0;
    }
    .banner::after {
      content: ""; position: absolute; top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0, 20, 50, 0.7);
    }
    .banner-content {
      position: relative; z-index: 2;
      height: 100%; display: flex;
      align-items: center; justify-content: center;
      flex-direction: column; text-align: center; color: white;
    }
    .transicao-para-azul {
  height: 120px;
  margin-top: -100px;
  background: linear-gradient(to bottom, rgba(0, 20, 50, 0), #001f3f);
  position: relative;
  z-index: 1;
}

    .aba-cursos {
      padding: 60px 20px;
      background-color: #001f3f;
    }
    .aba-cursos h2 {
      text-align: center;
      font-size: 28px;
      color: gold;
      margin-bottom: 40px;
    }
    .cursos-retangulos {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 25px;
    }
    .curso-retangulo {
      flex: 1 1 250px;
      max-width: 300px;
      background-color: #002d5c;
      padding: 70px 25px 45px 25px;
      border-radius: 12px;
      text-align: center;
      box-shadow: 0 0 12px rgba(0,0,0,0.5);
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .curso-retangulo i {
      font-size: 40px;
      color: gold;
      margin-bottom: 15px;
    }
    .curso-retangulo h3 {
      margin-bottom: 12px;
      font-size: 22px;
      font-weight: bold;
      color: white;
    }
    .curso-retangulo p {
      margin-bottom: 20px;
      font-size: 14px;
      color: #ddd;
      line-height: 1.4;
      flex-grow: 1;
    }
    .botao {
      display: inline-block;
      padding: 10px 22px;
      background-color: #004080;
      color: white;
      font-weight: bold;
      border-radius: 6px;
      text-decoration: none;
      transition: background 0.3s;
    }
    .botao:hover {
      background-color: gold;
      color: #001f3f;
    }

    section.curso-detalhado {
      max-width: 800px;
      margin: 60px auto 80px auto;
      background-color: #001933;
      padding: 30px 25px;
      border-radius: 12px;
      box-shadow: 0 0 20px rgba(0,0,0,0.6);
      color: #ccc;
      display: none;
    }
    section.curso-detalhado.ativa {
      display: block;
    }
    section.curso-detalhado h2 {
      color: gold;
      margin-bottom: 15px;
      font-size: 32px;
      text-align: center;
    }
    section.curso-detalhado p {
      font-size: 16px;
      line-height: 1.6;
      text-align: justify;
      margin-bottom: 20px;
    }

    /* Novo layout das imagens maiores e sem textos ao lado */
    .curso-layout-colunas {
      display: flex;
      flex-direction: column;
      gap: 30px;
      margin-top: 30px;
      align-items: center;
    }
    .curso-layout-colunas img {
      width: 100%;
      max-width: 700px;
      border-radius: 12px;
      box-shadow: 0 0 20px rgba(255, 215, 0, 0.7);
      object-fit: cover;
    }

    @media (max-width: 768px) {
      .curso-layout-colunas img {
        max-width: 100%;
      }
    }

    .botao-voltar {
      display: block;
      margin: 30px auto 0 auto;
      padding: 12px 30px;
      background-color: gold;
      color: #001f3f;
      font-weight: bold;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-size: 16px;
      max-width: 200px;
      text-align: center;
      text-decoration: none;
    }
    .botao-voltar:hover {
      background-color: #e6c200;
    }

    #contato {
      background-color: #001933;
      padding: 60px 20px;
      color: white;
      text-align: center;
    }
    #contato h2 {
      font-size: 28px;
      color: gold;
      margin-bottom: 20px;
    }
    #contato p, #contato .endereco {
      font-size: 16px;
      color: #ccc;
      max-width: 600px;
      margin: 0 auto 30px;
    }
    #contato .whatsapp {
      display: inline-block;
      margin: 20px auto;
      padding: 12px 24px;
      background-color: #25d366;
      color: white;
      font-weight: bold;
      border-radius: 6px;
      text-decoration: none;
    }
    #contato .form-container {
      margin-top: 40px;
      max-width: 500px;
      margin-left: auto;
      margin-right: auto;
      text-align: left;
    }
    #contato input, #contato textarea {
      width: 100%;
      padding: 12px;
      margin-bottom: 15px;
      border-radius: 6px;
      border: none;
    }
    #contato button {
      margin-top: 15px;
      padding: 12px 24px;
      background-color: #004080;
      color: white;
      font-weight: bold;
      border-radius: 6px;
      border: none;
      cursor: pointer;
      width: 100%;
      font-size: 16px;
    }
    #contato button:hover {
      background-color: gold;
      color: #001f3f;
    }
    #contato iframe {
      width: 100%;
      height: 300px;
      border: none;
      border-radius: 6px;
      margin: 30px auto;
      max-width: 500px;
      display: block;
    }
    .redes {
      margin-top: 20px;
      text-align: center;
    }
    .redes a {
      color: white;
      margin: 0 10px;
      font-size: 28px;
      text-decoration: none;
      transition: color 0.3s;
    }
    .redes a:hover {
      color: gold;
    }
  </style>
</head>
<body>

  <header>
    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSdHoxKQU94wsGRBwVylYtD7CQhYcnZ0Z1xOg&s" alt="Logo da Escola" />
    <div class="titulo-escola">
      <span>Escola</span>
      <span>Neusa Pimentel</span>
      <span>Barbosa</span>
    </div>
  </header>

  <nav>
    <div class="hamburger" id="hamburger">
      <div></div>
      <div></div>
      <div></div>
    </div>
    <ul id="menu">
      <li><a href="#">Início</a></li>
      <li id="cursos-menu">
        <a href="#cursos">Cursos <i class="fas fa-caret-down" style="margin-left:5px;"></i></a>
        <ul class="submenu">
          <li><a href="#curso-desenvolvimento">Desenvolvimento de Sistemas</a></li>
          <li><a href="#curso-agro">Agro</a></li>
          <li><a href="#curso-logistica">Logística</a></li>
          <li><a href="#curso-seguranca">Segurança do Trabalho</a></li>
        </ul>
      </li>
      <li><a href="#contato">Contato</a></li>
    </ul>
  </nav>

  <div class="transicao-para-imagem"></div>

  <div class="banner">
    <div class="banner-content">
      <h1>Bem-vindo à Escola Neusa Pimentel Barbosa</h1>
      <p>Formando profissionais para o futuro</p>
    </div>
  </div>

  <div class="transicao-para-azul"></div>

  <section id="cursos" class="aba-cursos">
    <h2>Nossos Cursos</h2>
    <div class="cursos-retangulos">

      <div class="curso-retangulo">
        <i class="fas fa-laptop-code"></i>
        <h3>Desenvolvimento de Sistemas</h3>
        <p>Curso focado em programação, desenvolvimento de softwares e aplicações modernas para diferentes plataformas. Ideal para quem quer criar soluções digitais eficientes.</p>
        <a href="#curso-desenvolvimento" class="botao">Saiba Mais</a>
      </div>

      <div class="curso-retangulo">
        <i class="fas fa-tractor"></i>
        <h3>Agro</h3>
        <p>Aprenda técnicas agrícolas sustentáveis, manejo de culturas e gestão no agronegócio para impulsionar a produção rural com responsabilidade ambiental.</p>
        <a href="#curso-agro" class="botao">Saiba Mais</a>
      </div>

      <div class="curso-retangulo">
        <i class="fas fa-boxes"></i>
        <h3>Logística</h3>
        <p>Aborda transporte, armazenagem e distribuição de mercadorias para otimizar a cadeia de suprimentos, garantindo eficiência e economia.</p>
        <a href="#curso-logistica" class="botao">Saiba Mais</a>
      </div>

      <div class="curso-retangulo">
        <i class="fas fa-hard-hat"></i>
        <h3>Segurança do Trabalho</h3>
        <p>Ensina normas e práticas para garantir ambientes laborais seguros, prevenindo acidentes e promovendo a saúde dos trabalhadores.</p>
        <a href="#curso-seguranca" class="botao">Saiba Mais</a>
      </div>
<!-- Nossas Instalações -->
<section class="nossas-instalacoes">
  <h2>Nossas Instalações</h2>
  <div class="instalacoes-grid">

<div class="instalacao-item">
    <img src="https://lens.usercontent.google.com/image?vsrid=CLSL3bKHlfqCZxACGAEiJDJhMWRkMmM0LTdmYTYtNGM3Ni04MGYxLWQ2ZTM4YjE0MzY0NDIGIgJjZigPOPnx2-34wY4D&gsessionid=hVvWw3AUjKKgbHS-LeG-2LSpRS_0NeW1jdiVq3Nh5PhuWsQ1fJVt7A" alt="Quadra">
      <div class="overlay">
        <h3>Quadra de Esportes</h3>
        <p>Local para aulas de educação física, campeonatos internos e atividades recreativas.</p>
      </div>
    </div>

    <div class="instalacao-item">
      <img src="https://images.unsplash.com/photo-1589923188900-59a9d7c2b67d?auto=format&fit=crop&w=800&q=80" alt="Refeitório" />
      <div class="overlay">
        <h3>Refeitório</h3>
        <p>Ambiente limpo e organizado onde os alunos realizam suas refeições com qualidade e conforto.</p>
      </div>
    </div>

    <div class="instalacao-item">
      <img src="https://images.unsplash.com/photo-1577896851231-70ef18881754?auto=format&fit=crop&w=800&q=80" alt="Biblioteca" />
      <div class="overlay">
        <h3>Biblioteca</h3>
        <p>Espaço silencioso com acervo diversificado para leitura, pesquisa e estudo.</p>
      </div>
    </div>

    <div class="instalacao-item">
      <img src="https://images.unsplash.com/photo-1581090700227-1e8a674561d2?auto=format&fit=crop&w=800&q=80" alt="Laboratório" />
      <div class="overlay">
        <h3>Laboratório</h3>
        <p>Ambiente equipado para aulas práticas de ciências e informática.</p>
      </div>
    </div>

    <div class="instalacao-item">
      <img src="https://images.unsplash.com/photo-1614797439637-d3b11aa1b29c?auto=format&fit=crop&w=800&q=80" alt="Mesas de Tóto" />
      <div class="overlay">
        <h3>Mesas de Esportes</h3>
        <p>Área com pebolim e jogos de mesa para momentos de descontração e lazer dos alunos.</p>
      </div>
    </div>

    <div class="instalacao-item">
      <img src="https://images.unsplash.com/photo-1595254080023-2c1ffb1a89d5?auto=format&fit=crop&w=800&q=80" alt="Horta Escolar" />
      <div class="overlay">
        <h3>Horta Escolar</h3>
        <p>Espaço sustentável onde os alunos aprendem sobre cultivo, alimentação saudável e meio ambiente.</p>
      </div>
    </div>

  </div>
</section>

<style>
  .nossas-instalacoes {
    padding: 60px 20px;
    background-color: #001f3f;
  }

  .nossas-instalacoes h2 {
    text-align: center;
    font-size: 28px;
    color: gold;
    margin-bottom: 40px;
  }

  .instalacoes-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 3 colunas fixas */
    gap: 25px;
    max-width: 1100px;
    margin: 0 auto;
  }

  .instalacao-item {
    position: relative;
    overflow: hidden;
    border-radius: 12px;
    box-shadow: 0 0 12px rgba(0,0,0,0.5);
  }

  .instalacao-item img {
    width: 100%;
    height: 280px; /* Aumentado */
    object-fit: cover;
    display: block;
    border-radius: 12px;
    transition: transform 0.4s ease;
  }

  .instalacao-item:hover img {
    transform: scale(1.05);
  }

  .instalacao-item .overlay {
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0, 40, 80, 0.6);
    color: white;
    padding: 20px;
    opacity: 0;
    transition: opacity 0.4s ease;
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    border-radius: 12px;
  }

  .instalacao-item:hover .overlay {
    opacity: 1;
  }

  .instalacao-item .overlay h3 {
    font-size: 20px;
    margin-bottom: 10px;
    color: gold;
  }

  .instalacao-item .overlay p {
    font-size: 14px;
    color: #ddd;
  }

  @media (max-width: 768px) {
    .instalacoes-grid {
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    }
  }
</style>

    </div>
  </section>

  <!-- Seções individuais dos cursos com imagens maiores e mais informações -->
  <section id="curso-desenvolvimento" class="curso-detalhado">
    <h2>Desenvolvimento de Sistemas</h2>
    <p>Este curso prepara o aluno para atuar no desenvolvimento de soluções tecnológicas inovadoras, usando as mais atuais linguagens e ferramentas de programação. Além do aprendizado técnico, há foco em trabalho em equipe, metodologias ágeis e resolução de problemas.</p>
    <p>Durante o curso, o aluno poderá participar de projetos reais, hackathons e estágios em empresas parceiras, ampliando suas oportunidades profissionais.</p>

    <div class="curso-layout-colunas">
      <img src="https://images.unsplash.com/photo-1519389950473-47ba0277781c?auto=format&fit=crop&w=800&q=80" alt="Alunos programando" />
      <img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?auto=format&fit=crop&w=800&q=80" alt="Projeto de software" />
    </div>

    <a href="#cursos" class="botao-voltar">← Voltar para Cursos</a>
  </section>

  <section id="curso-agro" class="curso-detalhado">
    <h2>Agro</h2>
    <p>Com enfoque em sustentabilidade e inovação, o curso Agro oferece conhecimentos práticos e teóricos para quem deseja contribuir com o crescimento do agronegócio regional. Os alunos aprendem desde técnicas de plantio até gestão financeira do agronegócio.</p>
    <p>O curso também oferece visitas técnicas e participação em projetos de pesquisa agrícola com instituições parceiras.</p>

    <div class="curso-layout-colunas">
      <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=800&q=80" alt="Trator no campo" />
      <img src="https://images.unsplash.com/photo-1494526585095-c41746248156?auto=format&fit=crop&w=800&q=80" alt="Cultivo agrícola" />
    </div>

    <a href="#cursos" class="botao-voltar">← Voltar para Cursos</a>
  </section>

  <section id="curso-logistica" class="curso-detalhado">
    <h2>Logística</h2>
    <p>Este curso forma profissionais capazes de gerenciar processos logísticos complexos, desde o planejamento até a execução e controle da cadeia de suprimentos. Inclui o uso de tecnologias para otimizar operações e reduzir custos.</p>
    <p>Estágios em empresas do setor e simulações práticas complementam o aprendizado teórico, garantindo preparo para o mercado.</p>

    <div class="curso-layout-colunas">
      <img src="https://images.unsplash.com/photo-1542834369-f10ebf06d3cb?auto=format&fit=crop&w=800&q=80" alt="Armazém logístico" />
      <img src="https://images.unsplash.com/photo-1515165562835-c1ee97f1de2e?auto=format&fit=crop&w=800&q=80" alt="Gestão de estoque" />
    </div>

    <a href="#cursos" class="botao-voltar">← Voltar para Cursos</a>
  </section>

  <section id="curso-seguranca" class="curso-detalhado">
    <h2>Segurança do Trabalho</h2>
    <p>Curso focado na formação de profissionais capacitados para identificar riscos, implementar normas de segurança e promover a saúde ocupacional. Aulas práticas, simulações e visitas técnicas fazem parte da formação.</p>
    <p>Parcerias com empresas locais garantem estágios e maior inserção no mercado de trabalho.</p>

    <div class="curso-layout-colunas">
      <img src="https://images.unsplash.com/photo-1596495578060-c600a4de69d7?auto=format&fit=crop&w=800&q=80" alt="Equipamento de segurança" />
      <img src="https://images.unsplash.com/photo-1532619675605-6a5b2c7c0896?auto=format&fit=crop&w=800&q=80" alt="Treinamento segurança" />
    </div>

    <a href="#cursos" class="botao-voltar">← Voltar para Cursos</a>
  </section>

  <!-- Aba Contato -->
  <section id="contato">
    <h2>Contato</h2>
    <p>Entre em contato conosco para tirar dúvidas ou agendar uma visita.</p>
    <p class="endereco">Rua Zita da Silva Neiva, s/n, Prado, Paracatu, Minas Gerais, CEP 38602-026</p>
    <a href="https://wa.me/5598987654321" target="_blank" rel="noopener" class="whatsapp">Fale conosco pelo WhatsApp</a>

    <div class="form-container">
      <form action="#" method="POST">
        <input type="text" name="nome" placeholder="Seu nome" required />
        <input type="email" name="email" placeholder="Seu e-mail" required />
        <textarea name="mensagem" rows="5" placeholder="Sua mensagem" required></textarea>
        <button type="submit">Enviar</button>
      </form>
    </div>

    <iframe
      src="https://maps.google.com/maps?q=Rua%20Zita%20da%20Silva%20Neiva%2C%20Prado%2C%20Paracatu%2C%20MG&t=&z=15&ie=UTF8&iwloc=&output=embed"
      loading="lazy"
      referrerpolicy="no-referrer-when-downgrade"
    ></iframe>
    <div class="redes">
      <a href="#" aria-label="Facebook"><i class="fab fa-facebook"></i></a>
      <a href="#" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
      <a href="#" aria-label="LinkedIn"><i class="fab fa-linkedin"></i></a>
    </div>
  </section>

  <script>
    // Menu hambúrguer mobile
    const hamburger = document.getElementById('hamburger');
    const menu = document.getElementById('menu');
    hamburger.addEventListener('click', () => {
      hamburger.classList.toggle('open');
      menu.classList.toggle('open');
    });

    // Abrir submenu no mobile via clique
    const cursosMenuLi = document.getElementById('cursos-menu');
    cursosMenuLi.querySelector('a').addEventListener('click', e => {
      if(window.innerWidth <= 768){
        e.preventDefault();
        cursosMenuLi.classList.toggle('submenu-open');
      }
    });

    // Controle de abas para mostrar só o conteúdo do curso detalhado clicado
    const linksCursos = document.querySelectorAll('#cursos-menu ul.submenu li a');
    const abaCursos = document.getElementById('cursos');
    const todasSecoes = document.querySelectorAll('section.curso-detalhado');

    linksCursos.forEach(link => {
      link.addEventListener('click', e => {
        e.preventDefault();
        const targetId = link.getAttribute('href').substring(1);

        // Esconde a lista de cursos principal
        abaCursos.classList.add('oculto');

        // Esconde todas as seções detalhadas
        todasSecoes.forEach(sec => sec.classList.remove('ativa'));

        // Mostra a seção detalhada escolhida
        const targetSection = document.getElementById(targetId);
        if (targetSection) {
          targetSection.classList.add('ativa');
          targetSection.scrollIntoView({ behavior: 'smooth' });
        }
      });
    });

    // Botão voltar para a lista de cursos em cada seção detalhada
    todasSecoes.forEach(sec => {
      const btnVoltar = sec.querySelector('.botao-voltar');
      btnVoltar.addEventListener('click', () => {
        sec.classList.remove('ativa');
        abaCursos.classList.remove('oculto');
        abaCursos.scrollIntoView({ behavior: 'smooth' });
      });
    });
  </script>
</body>
</html>
