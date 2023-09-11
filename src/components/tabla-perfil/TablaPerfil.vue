<template>
  <div>
    <div class="container contenedor">
      <table class="table table-striped">
        <thead>
          <tr class="tabla-titulo">
            <th scope="col">
              NOMBRE DEL PERFIL
              <img
                src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/cd6b9dcb-f542-4385-9404-65ef6bdb0bbd/original/Vector.svg"
                alt="chevron-expand"
                class="chevron-expand"
              >
            </th>
            <th scope="col">
              ESTATUS
              <img
                src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/cd6b9dcb-f542-4385-9404-65ef6bdb0bbd/original/Vector.svg"
                alt="chevron-expand"
                class="chevron-expand"
              >
            </th>
            <th scope="col">
              FECHA ÚLTIMA DE MODIFICACIÓN
              <img
                src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/cd6b9dcb-f542-4385-9404-65ef6bdb0bbd/original/Vector.svg"
                alt="chevron-expand"
                class="chevron-expand"
              >
            </th>
            <th scope="col">
              CREA SOLICITUDES
              <img
                src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/cd6b9dcb-f542-4385-9404-65ef6bdb0bbd/original/Vector.svg"
                alt="chevron-expand"
                class="chevron-expand"
              >
            </th>
            <th scope="col">
              ACCIONES
            </th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="perfil in dataPerfiles"
            :key="perfil"
            class="columna-contenido"
          >
            <td>{{ perfil.nombrePerfil }}</td>
            <td class="estilo-estatus">
              <img
                src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/5cf9f410-ad2d-4808-883c-a93f60b8bc52/original/Ellipse_26.svg"
                alt=""
              > 
              {{ perfil.estatus }}
            </td>
            <td>{{ perfil.fechaModificacion }}</td>
            <td>{{ perfil.creaSolicitudes }}</td>
            <td>
              <button
                id="btn-acciones"
                class="btn-estilo"
                @click="openAcciones(perfil.id)"
              >
                <img
                  src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/a589812c-888b-4df8-ac8a-35189df65b33/original/Vector.svg"
                  alt=""
                >
              </button>
            </td>
            <div class="acciones-perfil">
              <acciones-perfil
                :id_perfil="perfil.id"
                :mostrar-tarjeta="mostrarTarjeta"
                :mostrar-boton-cerrar="false"
                @cerrar-tarjeta="openAcciones"
              />
            </div>
          </tr> 
        </tbody>
      </table>
      
      
      <div class="pag-text">
        <p
          href=""
          style="color:rgb(173, 169, 169)"
        >
          Mostrando 1 de 50 páginas
        </p>      
        <div class="paginacion">
          <div
            :class="{'previusDisabled':previusDisabled}"
          >
            <span class="icono-pag">&#8592;</span>
            <button
              class="boton-pag"
              @click="previusPage()"
            >
              <strong>Ant.</strong>
            </button>
          </div>

          <div
            v-for="pagina in totalPages"
            :key="pagina"
          >
            <button
              class="boton-pag "
              :class="{ 'num': selected === pagina}"
              @click="paginateSelected(pagina)"
            >
              {{ pagina }}
            </button>
          </div>
          
          
          <div
            :class="{'nextDisabled':nextDisabled}"
          >
            <button
              class="boton-pag"
              @click="nextPage()"
            >
              <strong>Sig</strong>
            </button>
            <span class="icono-pag">&#8594;</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
  
  <script>
  import '@/publico/css/tabla-perfil/tabla-perfil.css';
  import AccionesPerfil from  '../acciones-perfil/AccionesPerfil.vue'
 // import axios from 'axios';
  export default{
      name:'TablaPerfil',
      components:{
        AccionesPerfil
      },
      data(){
      return{
       dataPerfiles:[],
       mostrarTarjeta: 0,
       perfilesPorPagina:5,
       paginaActual:1,
       totalPerfiles:0,
       selected: 1,
       totalPages:3,
       previusDisabled:true,
       nextDisabled:false
      }
      }, 
      computed:{

        perfilesPaginados() {
        const inicio = (this.paginaActual - 1) * this.perfilesPorPagina;
        const fin = inicio + this.perfilesPorPagina;
        return this.dataPerfiles.slice(inicio, fin);
      },

      totalPaginas() {
      return Math.ceil(this.totalPerfiles / this.perfilesPorPagina);
      },

      },
      mounted(){
          this.getPerfiles();
      },
      methods:{
          getPerfiles(){
              this.dataPerfiles=[
  {
    "id": 1,
    "nombrePerfil": "Administrador",
    "estatus": "Activo",
    "fechaModificacion": "24/05/2023",
    "creaSolicitudes": "Si"
  },
  {
    "id": 2,
    "nombrePerfil": "Promotor BP",
    "estatus": "Activo",
    "fechaModificacion": "24/05/2023",
    "creaSolicitudes": "Si"
  },
  {
    "id": 3,
    "nombrePerfil": "Promotor BE",
    "estatus": "Activo",
    "fechaModificacion": "24/05/2023",
    "creaSolicitudes": "Si"
  },
  {
    "id": 4,
    "nombrePerfil": "Administrador",
    "estatus": "Activo",
    "fechaModificacion": "25/05/2023",
    "creaSolicitudes": "Si"
  },
  {
    "id": 5,
    "nombrePerfil": "Promotor BP",
    "estatus": "Activo",
    "fechaModificacion": "25/05/2023",
    "creaSolicitudes": "Si"
  },
  {
    "id": 6,
    "nombrePerfil": "Promotor BE",
    "estatus": "Activo",
    "fechaModificacion": "25/05/2023",
    "creaSolicitudes": "Si"
  },
  {
    "id": 7,
    "nombrePerfil": "Administrador",
    "estatus": "Activo",
    "fechaModificacion": "26/05/2023",
    "creaSolicitudes": "Si"
  },
  {
    "id": 8,
    "nombrePerfil": "Promotor BP",
    "estatus": "Activo",
    "fechaModificacion": "26/05/2023",
    "creaSolicitudes": "Si"
  },
  {
    "id": 9,
    "nombrePerfil": "Promotor BE",
    "estatus": "Activo",
    "fechaModificacion": "26/05/2023",
    "creaSolicitudes": "Si"
  },
  {
    "id": 10,
    "nombrePerfil": "Administrador",
    "estatus": "Activo",
    "fechaModificacion": "27/05/2023",
    "creaSolicitudes": "Si"
  }
]


             /*
             LLAMAR AL API
             console.log("obteniendo perfiles");
             axios.get('http://localhost:3000/perfiles').then(response => {
             this.dataPerfiles = response.data;
             this.totalPerfiles = this.dataPerfiles.length;
             console.log("response->",response);

             }).catch(error => {
              console.log("error json-",error);
              });*/
          },
          mensaje(){
              console.log("Ejecutando desde el padre");
          },

          openAcciones(idPerfil){
          if(idPerfil == this.mostrarTarjeta){
            this.mostrarTarjeta=0;
          }else{
            this.mostrarTarjeta=idPerfil;
          }
          //this.mostrarTarjeta = !this.mostrarTarjeta;
          console.log("si funciona")
        },

        paginateSelected(pagina){
          this.selected=pagina;
          this.validatePreviusPage();
          this.validateNextPage();
        },

        nextPage(){
          if(this.selected<this.totalPages){
            this.selected+=1;
          }
          this.validatePreviusPage();
          this.validateNextPage();
        },
        previusPage(){
          if(this.selected>1){
            this.selected-=1;
          }
          this.validatePreviusPage();
          this.validateNextPage();
        },
        validatePreviusPage(){
            if(this.selected>1){
              this.previusDisabled=false;
            }else{
              this.previusDisabled=true;
            }
        },

        validateNextPage(){
          console.log(this.selected)
            if(this.selected<this.totalPages){
              this.nextDisabled=false;
            }else{
              this.nextDisabled=true;
            }
        }
      },

      init(){
        alert("Hola");
         this.validateInitPages();
      
      },

      validateInitPages(){
         if(this.totalPages == 1){
           this.nextDisabled=true;
           this.previusDisabled=true;
         }   
      },


  }
  </script>