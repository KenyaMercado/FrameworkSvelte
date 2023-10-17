<body>
  <div id="app">
    <aside class="sidebar" class:open="{isSidebarOpen}">
      <button on:click={toggleSidebar} class="toggle-button">
        <span></span>
        <span></span>
        <span></span>
      </button>
      <nav class="nav-menu">
        <ul>
          <li><a href="#accesorios">Accesorios</a></li>
          <li><a href="#Sportster">Novedad</a></li>
          <li><a href="#acerca-de-nosotros">Acerca de Nosotros</a></li>
        </ul>
      </nav>
    </aside>
    <header class="header">
      <button on:click={toggleSidebar} class="toggle-button">
        <span></span>
        <span></span>
        <span></span>
      </button>
      <h1>Cycle World</h1>
    </header>
    <div class="image-container">
      <img id="fondo" src="/moto1.jpg" alt="Cycle World Image" />
    </div>
    <div class="best-sellers" id="accesorios">
      <h2>Accesorios</h2>
      <div class="best-sellers-images">
        <div class="best-seller-item">
          <img src="/casco.jpg" alt="Producto 1" />
        </div>
        <div class="best-seller-item">
          <img src="/chaleco.png" alt="Producto 2" />
        </div>
        <div class="best-seller-item">
          <img src="/guantes.jpg" alt="Producto 3" />
        </div>
        <div class="best-seller-item">
          <img src="/casco2.jpg" alt="Producto 4" />
        </div>
      </div>
    </div>
	<div class="wide-container" id="Sportster">
		<h2>Sportster S 2023</h2>
		<img src="/moto2.jpg" class="wide-image"/>
	</div>
    <div class="about-us" id="acerca-de-nosotros">
      <h2>Acerca de nosotros</h2>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec sed vehicula mauris. Donec convallis nec velit sit amet molestie.
		Maecenas a tellus tristique, tincidunt metus eget, posuere dolor. Mauris finibus tempus tellus, at sagittis dui sollicitudin ac.
		Donec viverra nec augue id pretium. Proin maximus, purus vel bibendum volutpat, elit lorem commodo tortor, vel lacinia lacus nisi non diam.
		Morbi vel sem nec leo tempus euismod. Suspendisse placerat quam id justo tincidunt, eu dapibus orci finibus. In in imperdiet est. 
		Sed elementum volutpat semper. Proin eget ipsum turpis. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec accumsan, lacus at
		dignissim posuere, ligula lorem finibus ipsum, in fermentum nulla est eget urna. Aliquam venenatis nisl sit amet dapibus tincidunt. 
		Nam varius, nisl nec pellentesque bibendum, nibh elit feugiat eros, non pellentesque lacus lacus quis ipsum. Ut porttitor lorem non felis 
		mattis accumsan.
      </p>
    </div>
  </div>
</body>

<script>
  let currentImage = 0;
  let showImage = true;
  let isSidebarOpen = false;

  const images = [
    '/moto1.jpg',
  ];
  let src = images[currentImage];
  let alt = 'Cycle World Image';

  function startImageAnimation() {
    setInterval(() => {
      showImage = false;
      setTimeout(() => {
        currentImage = (currentImage + 1) % images.length;
        src = images[currentImage];
        showImage = true;
      }, 4000); // Muestra la nueva imagen durante 2 segundos antes de cambiar
    }, 5000); // Cambia la imagen cada 4 segundos
  }

  function toggleSidebar() {
    isSidebarOpen = !isSidebarOpen;
  }

  startImageAnimation();
</script>

<style>
	body {
	margin: 0;
	padding: 0;
	background-color: black;
	font-family: 'Lato', sans-serif;
	}
	.about-us {
	background-color: #F6F5F2; /* Fondo blanco */
	padding: 20px;
	text-align: justify;
	
	}

	.about-us h2 {
	font-size: 24px;
	text-align: center;
	color: black; /* Color de texto */
	}

	.about-us p {
	font-size: 18px;
	color: black; /* Color de texto */
	}
	.image-container {
	text-align: center;
	overflow: hidden; 
	height: 125vh;
	}

	/* Estilos CSS para la imagen */
	img {
	background-size:cover;
	max-width: 100%; 
	height: auto;
	}

	#fondo {
		background-size:cover;
		width: 100%; 
		height: 100%;
	}

	.slide-enter-active,
	.slide-leave-active {
	transition: transform 2s ease; /* Duración de la animación y tipo de transición */
	}

	.slide-enter-to {
	transform: translateX(0); 
	}

	.sidebar {
	position: fixed;
	left: -300px; /* Inicialmente oculto */
	top: 0;
	height: 100%;
	width: 300px;
	background-color: #333; 
	overflow-x: hidden;
	overflow-y: auto;
	z-index: 2; 
	transition: 0.3s;
	display: flex;
	flex-direction: column;
	align-items: center;
	padding-top: 50px;
	}

	.sidebar.open {
	left: 0; /* Mostrar el menú al hacer clic en el botón */
	}

	.toggle-button {
	position: fixed;
	left: 5px;
	top: 10px;
	background-color: transparent;
	border: none;
	cursor: pointer;
	}

	.toggle-button span {
		display: block;
		width: 30px;
		height: 3px;
		background-color: white;
		margin: 6px 0;
		transition: 0.4s;
	}

	.toggle-button.open span:nth-child(1) {
		transform: rotate(-45deg) translate(-5px, 6px);
	}

	.toggle-button.open span:nth-child(2) {
		opacity: 0;
	}

	.toggle-button.open span:nth-child(3) {
		transform: rotate(45deg) translate(-5px, -6px);
	}

	/* Estilos para el menú de navegación */
	.nav-menu {
	margin-top: 20px;
	color: white;
	}

	.nav-menu ul {
	list-style: none;
	padding: 0;
	}

	.nav-menu ul li {
	margin: 10px 0;
	padding: 0;
	}

	.nav-menu ul li a {
	text-decoration: none;
	color: white;
	font-size: 18px;
	}

	.header {
	background-color: #000000;
	text-align: center;
	font-size: 25px;
	color: white;
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 20%;
	box-sizing: border-box;
	padding: 10px 0;
	}

	.best-sellers {
	background-color: #000; /* Fondo blanco */
	padding: 20px;
	text-align: center;
	}

	.best-sellers h2 {
	font-size: 26px;
	text-align: center;
	color: white; /* Color de texto */
	}

	.best-sellers-images {
	display: flex;
	justify-content: space-around;
	margin-top: 20px;
	}

	.best-seller-item {
	text-align: center;
	}

	.best-seller-item img {
	max-width: 100%; /* Asegura que las imágenes no sean muy grandes */
	height: auto;
	margin-bottom: 10px;
	padding: 5px; /* Espaciado alrededor de las imágenes */
	filter: grayscale(0%); /* Aplica el filtro de opacidad gris */
	transition: filter 0.3s ease;
	}

	.best-seller-item img:hover {
	filter: grayscale(80%); /* Elimina el filtro al pasar el mouse sobre la imagen */
	}


	.wide-container {
	text-align: center;
	background-color: white; /* Fondo blanco */
	padding: 10px;
	}

	.wide-container h2 {
	font-size: 24px;
	text-align: center;
	color: black;
	}

	.wide-image {
	background-size:cover;
	}

	
</style>
