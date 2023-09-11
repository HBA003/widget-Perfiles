<template>
  <div class="">
    <div class="home-header">
      <img
        src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/b45a8fe4-7369-46c1-937f-40e77314dade/original/invex-logo.svg"
        alt="text invex"
        class="img-text-invex"
      >
      <div class="user-header">
        <span class="text-userHerader" />
        <div class="user-container">
          <span class="user"><strong>Cristina Martínez</strong></span>
          <div class="ultima-conexion">
            <p>
              último acceso: 08/05/2023 10:25 a.m.
            </p>
          </div>
          <div class="user-icon">
            <p
              id="nombreUsuario"
              class=" nom-usuario"
            />
            <img
              id="iconoDesplegar"
              src="https://cloud.modyocdn.com/uploads/0bda3dcf-a592-4af6-98a5-e59059af340e/original/icon-desplegable.png"
              alt="icon desplegable"
              class="icon-desplegable"
              @click="inconoDesp()"
            >
          </div>
        </div>
      </div>
    </div>  
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div
        id="navbarNavAltMarkup"
        class="collapse navbar-collapse nav-menu"
      >
        <div class="navbar-nav">
          <div
            id="id-configuracion"
            class="nav-item nav-link nav-perfil"
          >
            <p
              id="titulo-config"
              @click="mostrarConfiguracion()"
            >
              <strong>Administración</strong>
            </p>
            <div
              id="linea-config"
              class="linea-config"
            />
            <div
              id="conf-menu"
              class="conf-menu"
            >
              <ul>
                <a
                  class="list-nav"
                  href="#"
                  style="text-decoration: none;"
                  @click="ocultarSubMenu()"
                ><strong>Perfiles</strong></a>
              </ul>
              <ul>
                <a
                  class="list-nav"
                  href="#"
                  style="text-decoration: none;"
                  @click="ocultarSubMenu()"
                ><strong>Usuarios</strong></a>
              </ul>
              <ul>
                <a
                  class="list-nav"
                  href="#"
                  style="text-decoration: none;"
                  @click="ocultarSubMenu()"
                ><strong>Flujos</strong></a>
              </ul>
            </div>  
          </div>

          <div
            id="id-solucion"
            class="nav-item nav-link nav-perfil"
          >
            <p
              id="titulo-solucion"
              @click="mostrarSolucion()"
            >
              <strong>Soluciones</strong>
            </p>
            <div
              id="linea-solucion"
              class="linea-config"
            />
            <div
              id="solucion-menu"
              class="conf-menu"
            >
              <ul>
                <a
                  class="list-nav"
                  href="#"
                  style="text-decoration: none;"
                  @click="ocultarSubMenu()"
                >Perfiles</a>
              </ul>
              <ul>
                <a
                  class="list-nav"
                  href="#"
                  style="text-decoration: none;"
                  @click="ocultarSubMenu()"
                >Perfiles</a>
              </ul>
              <ul>
                <a
                  class="list-nav"
                  href="#"
                  style="text-decoration: none;"
                  @click="ocultarSubMenu()"
                >Perfiles</a>
              </ul>
            </div>  
          </div>

          <div
            id="id-validacion"
            class="nav-item nav-link nav-perfil"
          >
            <p
              id="titulo-validacion"
              @click="mostrarValidacion()"
            >
              <strong>Validaciones</strong>
            </p>
            <div
              id="linea-validacion"
              class="linea-config"
            />
            <div
              id="validacion-menu"
              class="conf-menu"
            >
              <ul>
                <a
                  class="list-nav"
                  href="#"
                  style="text-decoration: none;"
                  @click="ocultarSubMenu()"
                >Perfiles</a>
              </ul>
              <ul>
                <a
                  class="list-nav"
                  href="#"
                  style="text-decoration: none;"
                  @click="ocultarSubMenu()"
                >Perfiles</a>
              </ul>
              <ul>
                <a
                  class="list-nav"
                  href="#"
                  style="text-decoration: none;"
                  @click="ocultarSubMenu()"
                >Perfiles</a>
              </ul>
            </div>  
          </div>
        </div>
      </div>
    </nav>
    
    <div class="linea" />
    <agregar-perfil />
  </div>  
</template>
<script>
import '@/publico/css/header/header-component.css';
import AgregarPerfil from '../agregar-perfil/AgregarPerfil.vue';
export default {
  name:'HeaderComponent',
  components:{
    AgregarPerfil
    },
  data() {
    return {
      nombreUsuario: 'Cristina Martinez'
    }
  },
  mounted() {
    this.iniciar();
    document.addEventListener('click', this.eventeListener);
  },
  beforeDestroy() {
   document.removeEventListener('click', this.eventeListener);
  },

  methods: {
  iniciar (){
    console.log("Iniciando");
// mostrar configuracion
    const hiddenConfiguration = document.getElementById('conf-menu');
    hiddenConfiguration.style.display = 'none';

    const lineaConfig =document.getElementById('linea-config');
    lineaConfig.style.display='none';
// mostrar solucion
    const hiddenSolucion = document.getElementById('solucion-menu');
    hiddenSolucion.style.display = 'none';

    const lineaSolucion =document.getElementById('linea-solucion');
    lineaSolucion.style.display='none';

// mostrar solucion
    const hiddenValidacion = document.getElementById('validacion-menu');
    hiddenValidacion.style.display = 'none';

    const lineaValidacion =document.getElementById('linea-validacion');
    lineaValidacion.style.display='none';

    this.obtenerPrimerasLetras();
    

},
mostrarConfiguracion(){
    console.log("Ocultando configuracion")
    const hiddenConfiguration = document.getElementById('conf-menu');
    hiddenConfiguration.style.display = 'block';

    const lineaConfig =document.getElementById('linea-config');
    lineaConfig.style.display='block';

    const textoTitulo=document.getElementById('titulo-config');

    textoTitulo.style.color='rgba(164,1,51)';

    this.quitarEstiloSolucion();
    this.quitarEstiloValidacion();

},


mostrarSolucion(){
    console.log("mostrando solucion")
    const hiddenSolucion = document.getElementById('solucion-menu');
    hiddenSolucion.style.display = 'block';

    const lineaSolucion =document.getElementById('linea-solucion');
    lineaSolucion.style.display='block';

    const textoSolucion=document.getElementById('titulo-solucion');
    textoSolucion.style.color='rgba(164,1,51)';

    this.quitarEstiloConfiguracion();
    this.quitarEstiloValidacion();
},

mostrarValidacion(){
    const hiddenValidacion = document.getElementById('validacion-menu');
    hiddenValidacion.style.display = 'block';

    const lineaValidacion =document.getElementById('linea-validacion');
    lineaValidacion.style.display='block';

    const textoValidacion=document.getElementById('titulo-validacion');
    textoValidacion.style.color='rgba(164,1,51)';

    this.quitarEstiloConfiguracion();
    this.quitarEstiloSolucion();
},

quitarEstiloSolucion(){
    const hiddenSolucion = document.getElementById('solucion-menu');
    hiddenSolucion.style.display = 'none';

    const lineaSolucion =document.getElementById('linea-solucion');
    lineaSolucion.style.display='none';

    const textoSolucion=document.getElementById('titulo-solucion');
    textoSolucion.style.color='#000000';
},

quitarEstiloConfiguracion(){
    const hiddenConfiguration = document.getElementById('conf-menu');
    hiddenConfiguration.style.display = 'none';

    const lineaConfig =document.getElementById('linea-config');
    lineaConfig.style.display='none';

    const textoTitulo=document.getElementById('titulo-config');
    textoTitulo.style.color='#000000';
},

quitarEstiloValidacion(){
    const hiddenValidacion = document.getElementById('validacion-menu');
    hiddenValidacion.style.display = 'none';

    const lineaValidacion =document.getElementById('linea-validacion');
    lineaValidacion.style.display='none';

    const textoValidacion=document.getElementById('titulo-validacion');
    textoValidacion.style.color='#000000';
},
ocultarSubMenu(){
    const hiddenConfiguration = document.getElementById('conf-menu');
    hiddenConfiguration.style.display = 'none';

    const hiddenSolucion = document.getElementById('solucion-menu');
    hiddenSolucion.style.display = 'none';

    const hiddenValidacion = document.getElementById('validacion-menu');
    hiddenValidacion.style.display = 'none';

},

// siempre esta en escucha

obtenerPrimerasLetras(){
 console.log("Obteniendo las primeras letras")
 const nombreUsuario ="cristina ";
 const apellidos="martinez";


 const primeraLetraNombre = nombreUsuario.charAt(0);
 const primeraLetraApellido = apellidos.charAt(0);

 var response = primeraLetraNombre.toUpperCase()+primeraLetraApellido.toUpperCase()

  const nameUser = document.getElementById('nombreUsuario');
  nameUser.innerHTML = response;
},

//clic en la imagen desplegar...
inconoDesp(){
    console.log('clic en la imagen')
}

},

venteListener(event) {
  const elemento = document.querySelector('.navbar-nav');
  if (!elemento.contains(event.target)) {
    this.ocultarSubMenu();
  }
}

}

</script>