<template>
  <div class="container div-contenedor">
    <div class="div-cont-perfil">
      <p>Administración > </p>
      <p class="cont-perfil">
        Perfiles
      </p>
    </div>
    <div class="div-let-perfil">
      <span class="let-perfil"><strong>Perfiles</strong></span>
      <button
        id="openModalBtn"
        class="btnAgregar"
        @click="openModal"
      >
        + Crear Perfil
      </button>
    </div>
    <div
      id="myModal"
      :class="modal"
    > 
      <div modal-form>
        <div class="contenido-modal">
          <div class="contenido-modal-child">
            <h4 style="margin-bottom: 30px;">
              <b> Agregar nuevo perfil</b>
            </h4>
            <div
              class="form-group row"
              style="margin-bottom: 70px;"
            >
              <div class="col-sm-6">
                <input
                  id="nombrePerfil"
                  v-model="nombrePerfil"
                  placeholder="Nombre del perfil*"
                  :maxlength="nombrePerfileSizeMax"
                  type="text"
                  class="form-control input-ancho"
                  :class="{ 'inputBorderRed': esIncorrecto}"
                  @change="validarCampoNombrePerfil('caracteres fuera del rango')"
                >
              </div>
  
              <p
                class="text-mesaje"
                :class="estiloInput"
                style="color: red;"
              >
                {{ mensajePerfilInput }}
              </p>
              <div class="col-sm-6">
                <!--inicia option personalizado-->
                <div
                  class="ajuste-flecha select-style"
                  @click="showOptionsSolicitudes()"
                >
                  <label
                    class="label-select"
                    for="solicitudPerfil"
                    style="color: #000; margin-bottom: -5px; font-size: 12px;"
                  >Puede crear solicitudes</label>
                  <label
                    for=""
                    class="value-option"
                  >
                    {{ valueOptionSolicitudes }}
                  </label>
                  <img
                    class="flecha-down"
                    src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/b4f494d7-e1ba-4084-aeed-cec4cce57a30/original/ExpandirMas.svg"
                    data-target="#solicitudPerfil"
                    alt="flecha-desplegables"
                  >

                  <div
                    v-if="showSelectSolicitudes"
                    class="option-style"
                  >
                    <ul
                      v-for="option in solicitudesOptionList "
                      :key="option"
                      class="option-list"
                    >
                      <li @click="selectOptionSolicitud(option)">
                        {{ option }} <hr class="linea-option">
                      </li>
                    </ul>
                  </div>
                </div>
                <!--finaliza option personalizado-->
              </div>
            </div>
            <hr class="linea-perfil">

            <div>
              <h4 style="margin-bottom: 30px;">
                <b>Perfiles</b>
              </h4>
              <div
                class="form-group row"
                style="margin-bottom: 70px;"
              >
                <p
                  class="text-mesaje"
                  :class="estiloInput"
                  style="color: red;"
                >
                  {{ mensajePerfilInput }}
                </p>
                <div class="col-sm-6">
                  <!--inicia option personalizado-->
                  <div
                    class="ajuste-flecha select-style"
                    @click="showOptionsPerfiles()"
                  >
                    <label
                      class="label-select"
                      for="solicitudPerfil"
                      style="color: #000; margin-bottom: -5px; font-size: 12px;"
                    >Tipo de perfil</label>
                    <label
                      for=""
                      class="value-option"
                    >
                      {{ valueOptionPerfiles }}
                    </label>
                    <img
                      class="flecha-down"
                      src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/b4f494d7-e1ba-4084-aeed-cec4cce57a30/original/ExpandirMas.svg"
                      data-target="#solicitudPerfil"
                      alt="flecha-desplegables"
                    >

                    <div
                      v-if="showSelectPerfiles"
                      class="option-style"
                    >
                      <ul
                        v-for="option in perfilesOptionList "
                        :key="option"
                        class="option-list"
                      >
                        <li @click="selectOptionPerfil(option)">
                          {{ option }} <hr class="linea-option">
                        </li>
                      </ul>
                    </div>
                  </div>
                <!--finaliza option personalizado-->
                </div>
              </div>
            </div>

            <hr class="linea-perfil-tipo">

            <div>
              <h4 style="margin-bottom: 30px;">
                <b>Usuarios</b>
              </h4>
              <div
                class="form-group row"
                style="margin-bottom: 70px;"
              >
                <p
                  class="text-mesaje"
                  :class="estiloInput"
                  style="color: red;"
                >
                  {{ mensajePerfilInput }}
                </p>
                <div class="col-sm-6">
                  <!--inicia option personalizado-->
                  <div
                    class="ajuste-flecha select-style"
                    @click="showOptionsUsuarios()"
                  >
                    <label
                      class="label-select"
                      for="solicitudPerfil"
                      style="color: #000; margin-bottom: -5px; font-size: 12px;"
                    >Tipo de usuario</label>
                    <label
                      for=""
                      class="value-option"
                    >
                      {{ valueOptionUsuarios }}
                    </label>
                    <img
                      class="flecha-down"
                      src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/b4f494d7-e1ba-4084-aeed-cec4cce57a30/original/ExpandirMas.svg"
                      data-target="#solicitudPerfil"
                      alt="flecha-desplegables"
                    >

                    <div
                      v-if="showSelectUsuarios"
                      class="option-style"
                    >
                      <ul
                        v-for="option in usuariosOptionList "
                        :key="option"
                        class="option-list"
                      >
                        <li @click="selectOptionUsuario(option)">
                          {{ option }} <hr class="linea-option">
                        </li>
                      </ul>
                    </div>
                  </div>
                <!--finaliza option personalizado-->
                </div>
              </div>
            </div>

            <hr class="linea-perfil-tipo">

            <div>
              <h4 style="margin-bottom: 25px;">
                <b>Flujos</b>
              </h4>
              <div
                class="form-group row"
                style="margin-bottom: 70px;"
              >
                <p
                  class="text-mesaje"
                  :class="estiloInput"
                  style="color: red;"
                >
                  {{ mensajePerfilInput }}
                </p>
                <div class="col-sm-6">
                  <!--inicia option personalizado-->
                  <div
                    class="ajuste-flecha select-style"
                    @click="showOptionsFlujo()"
                  >
                    <label
                      class="label-select"
                      for="solicitudPerfil"
                      style="color: #000; margin-bottom: -5px; font-size: 12px;"
                    >Tipo de flujo</label>
                    <label
                      for=""
                      class="value-option"
                    >
                      {{ valueOptionFlujos }}
                    </label>
                    <img
                      class="flecha-down"
                      src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/b4f494d7-e1ba-4084-aeed-cec4cce57a30/original/ExpandirMas.svg"
                      data-target="#solicitudPerfil"
                      alt="flecha-desplegables"
                    >

                    <div
                      v-if="showSelectFlujos"
                      class="option-style"
                    >
                      <ul
                        v-for="option in flujosOptionList "
                        :key="option"
                        class="option-list"
                      >
                        <li @click="selectOptionFlujo(option)">
                          {{ option }} <hr class="linea-option">
                        </li>
                      </ul>
                    </div>
                  </div>
                <!--finaliza option personalizado-->
                </div>
              </div>
            </div>

            <hr class="linea-perfil-tipo">
            <div>
              <h4 style="margin-bottom: 30px;">
                <b>Solicitudes</b>
              </h4>
              <div
                class="form-group row"
                style="margin-bottom: 45px;"
              >
                <p
                  class="text-mesaje"
                  :class="estiloInput"
                  style="color: red;"
                >
                  {{ mensajePerfilInput }}
                </p>
                <div class="col-sm-6">
                  <p style="color: #000000; margin-bottom: 10px;">
                    Tipo de acceso*
                  </p>
                  <table class="table table-bordered">
                    <tbody>
                      <tr>
                        <td style="width: 50% !important;">
                          <button 
                            class="btn-tipo-acceso"
                            @click="ocultarNivelAcceso()"
                          >
                            Sin acceso
                          </button>
                          <img
                            style="float: right;"
                            src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/d78839dc-167d-406e-8916-a15d3f7650ed/original/chevron-down.svg"
                            alt=""
                          >
                        </td>
                      </tr>
                      <tr>
                        <td>
                          <button
                            class="btn-tipo-acceso"
                            @click="mostrarNivelAcceso()"
                          >
                            Solo lectura
                          </button>
                          <img
                            style="float: right; cursor: pointer;"
                            src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/d78839dc-167d-406e-8916-a15d3f7650ed/original/chevron-down.svg"
                            alt=""
                            @click="mostrarNivelAcceso()"
                          >
                        </td>
                      </tr>
                      <tr>
                        <td>
                          <button
                            class="btn-tipo-acceso"
                            @click="mostrarNivelAcceso()"
                          >
                            Edición
                          </button>
                          <img
                            style="float: right; cursor: pointer;"
                            src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/d78839dc-167d-406e-8916-a15d3f7650ed/original/chevron-down.svg"
                            alt=""
                            @click="mostrarNivelAcceso()"
                          >
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </div>
                <div
                  v-if="nivelAccesoSolicitudes"
                  class="col-sm-6"
                >
                  <p style="color: #000000; margin-bottom: 10px;">
                    Nivel de acceso*
                  </p>
                  <table class="table table-bordered">
                    <tbody>
                      <tr>
                        <td>Asignado al usuario</td>
                      </tr>
                      <tr>
                        <td>Todas las solicitudes</td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
            </div>

            <hr class="linea-perfil-solicitudes">

            <div>
              <h4 style="margin-bottom: 30px;">
                <b>Validaciones</b>
              </h4>
              <div
                class="form-group row"
                style="margin-bottom: 50px;"
              >
                <p
                  class="text-mesaje"
                  :class="estiloInput"
                  style="color: rgb(232, 4, 4);"
                >
                  {{ mensajePerfilInput }}
                </p>
                <div class="col-sm-6">
                  <p style="color: #000000; margin-bottom: 10px;">
                    Tipo de acceso*
                  </p>
                  <table class="table table-bordered">
                    <tbody>
                      <tr>
                        <td>
                          <button 
                            class="btn-tipo-acceso"
                            @click="ocultarAccesosUsuarios()"
                          >
                            Sin acceso
                          </button>
                          <img
                            style="float: right;"
                            src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/d78839dc-167d-406e-8916-a15d3f7650ed/original/chevron-down.svg"
                            alt=""
                          >
                        </td>
                      </tr>
                      <tr>
                        <td>
                          <button
                            class="btn-tipo-acceso"
                            @click="mostrarAccesosUsuarios()"
                          >
                            Solo lectura
                          </button>
                          <img
                            style="float: right; cursor: pointer;"
                            src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/d78839dc-167d-406e-8916-a15d3f7650ed/original/chevron-down.svg"
                            alt=""
                            @click="mostrarAccesosUsuarios()"
                          >
                        </td>
                      </tr>
                      <tr>
                        <td>
                          <button
                            class="btn-tipo-acceso"
                            @click="mostrarAccesosUsuarios()"
                          >
                            Edición
                          </button>
                          <img
                            style="float: right; cursor: pointer;"
                            src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/d78839dc-167d-406e-8916-a15d3f7650ed/original/chevron-down.svg"
                            alt=""
                            @click="mostrarAccesosUsuarios()"
                          >
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </div>
                <div
                  v-if="nivelAccesoUsuarios"
                  class="col-sm-6"
                >
                  <p style="color: #000000; margin-bottom: 10px;">
                    Nivel de acceso*
                  </p>
                  <table class="table table-bordered">
                    <tbody>
                      <tr>
                        <td>Asignado al usuario</td>
                      </tr>
                      <tr>
                        <td>Todas las solicitudes</td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
            </div>

            <p style="font-size: 18px; color: #0F89D3; ">
              * Campos obligatorios
            </p>

            <div class="div-buttons-export">
              <button
                class="button-cancel-changes"
                @click="closeModal()"
              >
                Cancelar
              </button>
              <button
                class="btn-save-changes"
                @click="crearPerfil()"
              >
                Crear perfil
              </button>
            </div>
          </div>
          <span
            class="closeModal"
            @click="closeModal()"
          >&times;</span>
        </div>
      </div>
    </div>
    <div>
      <div>
        <div class="div-buscar">
          <form
            class="d-flex"
            role="search"
          >
            <input
              class="input"
              type="search"
              placeholder="Buscar"
              aria-label="Buscar"
            >
            <img
              class="icono-buscar"
              src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/ccb3fd8e-609a-4289-b4b0-9d17c9352040/original/search_black_24dp_1.svg"
              alt=""
            >
          </form>
        </div>
        <div class="mostrar-tabla">
          <form id="columnForm">
            <label
              class="laber-mostrar"
              style="color: gray;"
              for="columnas"
            > Mostrar: </label>
            <select
              class="form-select form-select-sm select-opciones"
              aria-label=".form-select-sm example"
            >
              <option
                selected
                class="opcion-lista"
              >
                5 Perfiles 
              </option>
              <option value="1">
                <strong>10 Perfiles</strong>
              </option>
              <option value="2">
                <strong>15 Perfiles</strong>
              </option>
              <option value="3">
                <strong>20 Perfiles</strong>
              </option>
            </select>
            <img
              class="img-desplegable"
              src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/059031be-da3d-4617-952b-cacdeb211b86/original/Shape.svg"
              alt=""
            >
          </form>
        </div>
        <div class="div-boton">
          <button
            class="btn-exportar"
            @click="openExportar()"
          >
            <img
              class="icono-export"
              src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/eaace30c-88f2-4b6b-b4d7-2a4c33e240a3/original/Vector.svg"
              alt=""
            >
            Exportar
            <img
              class="icono-desplegable"
              src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/059031be-da3d-4617-952b-cacdeb211b86/original/Shape.svg"
              alt=""
            >
          </button>
        </div>
      </div>
    </div>
    <exportar-tabla
      :mostrar-card="mostrarCard"
    />

    <!--Agregando el componente de la tabla-->
    <tabla-perfil
      ref="tablaChild"
      :perfil-seleccionado="perfilSeleccionado"
    />
  </div>
</template>
  <script>
  import '@/publico/css/agregar-perfil/agregar-perfil.css';
  import axios from 'axios';
  import TablaPerfil from '../tabla-perfil/TablaPerfil.vue';
  import ExportarTabla from '../esportar-tabla/ExportarTabla.vue';
  
  //import TablaPerfil from '.tabla-perfil/TablaPerfil.vue';
  export default {
    name: 'AgregarPerfil',
    components:{
      TablaPerfil,
      ExportarTabla
    },
    data(){
       return{
        nombrePerfil:'',
        nombrePerfileSizeMax:50,
        nombrePerfileSizeMin:5,
        esIncorrecto:false,
        selectVacio:false,
        estiloInput:'Activo',
        modal:'close-modal',
        mensajePerfilInput:'',
        valorSelect:'',
        mostrarCard: false,
        nivelAccesoSolicitudes:false,
        nivelAccesoUsuarios: false,

        solicitudesOptionList:['Si','No'],
        showSelectSolicitudes:false,
        valueOptionSolicitudes:'Seleccionar',

        perfilesOptionList:['Sin acceso','Solo lectura','Edición'],
        showSelectPerfiles:false,
        valueOptionPerfiles:'Seleccionar',

        usuariosOptionList:['Sin acceso','Solo lectura','Edición'],
        showSelectUsuarios:false,
        valueOptionUsuarios:'Seleccionar',

        flujosOptionList:['Sin acceso','Solo lectura','Edición'],
        showSelectFlujos:false,
        valueOptionFlujos:'Seleccionar',

       }
    },
    methods:{
       validarCampoNombrePerfil(){
        let auxNombrePerfil=this.nombrePerfil.replace(/\s/g, '');
        let sizePerfile=auxNombrePerfil.length;
        if(sizePerfile<this.nombrePerfileSizeMin){
          console.log("tamano de letra  fuera del rango");
          this.esIncorrecto=true;
          this.estiloInput='fuera-rango';
          this.mensajePerfilInput='El nombre debe de tener mínimo de 5 letras';
          return false;
        }else{
          this.esIncorrecto=false;
          this.estiloInput='input-defecto'
          this.mensajePerfilInput='todo nice';
          return true;
        }
        
       },
  
       openModal(){
        this.modal='open-modal';
       },
       closeModal(){
        this.modal='close-modal';
        this.devolverCamposDefecto();
       },
       validateSelect(){
         if(this.valorSelect.length<=0){
           this.selectVacio=true;
            return false;
         }else{
          this.selectVacio=false;
          return true;
         }
       },
       crearPerfil(){
            let nombrePerfil=this.validarCampoNombrePerfil();
            let select=this.validateSelect();
            if(nombrePerfil && select){
                console.log("TODO CORRECTO");
                this.saveDatos();
                this.devolverCamposDefecto();
            }else{
              this.modal='close-modal';
              console.log("todo mal");
            }
             
       },
       saveDatos(){
       console.log("Guardando datos");
       /*Logica para guardar los datos a la tabla*/
       var fecha = new Date();

      // Obtener los componentes de la fecha
      var dia = fecha.getDate();
      var mes = fecha.getMonth() + 1; // Se suma 1 porque los meses se indexan desde 0
      var anio = fecha.getFullYear();

      // Añadir ceros iniciales si es necesario
      if (dia < 10) {
        dia = '0' + dia;
      }

      if (mes < 10) {
        mes = '0' + mes;
      }

      // Crear el formato de fecha
      var fechaFormateada = dia + '/' + mes + '/' + anio;

        let payload={
          id:this.getIdFiccion(),
          producto:this.nombrePerfil,
          estatus:"Activo",
          fechaUltimaConexion:fechaFormateada,
          creaSolicitudes:this.valorSelect, 
          acciones:"..."
        }
    
        axios.post('http://localhost:3000/perfiles',payload).then(response => {

          const componenteHijo = this.$refs.tablaChild;
          componenteHijo.getPerfiles();

         console.log('Datos guardados con éxito:', response);
         }).catch(error => {

             console.error('Error al guardar los datos:', error);

        });
        },
  
      devolverCamposDefecto(){
        console.log("vaciando campos");
        this.valorSelect='';
        this. nombrePerfil='';
        this.esIncorrecto=false;
        this.selectVacio=false;
        this.estiloInput='input-defecto';
        this.modal='close-modal';
      },
  
      getIdFiccion(){
        const fechaActual = new Date();
        const idUnico = fechaActual.getTime();
        console.log(idUnico);
  
      },

    openExportar() {
      if(this.mostrarCard === true){
        this.mostrarCard=false;
      }else{
        this.mostrarCard=true;
      }
    },

    mostrarNivelAcceso(){
      if(this.nivelAccesoSolicitudes ===true){
        this.nivelAccesoSolicitudes=false;
      }else{
        this.nivelAccesoSolicitudes=true;
      }
    },

    ocultarNivelAcceso(){
      this.nivelAccesoSolicitudes = false;
    },
    
    mostrarAccesosUsuarios(){
      if(this.nivelAccesoUsuarios ===true){
        this.nivelAccesoUsuarios=false;
      }else{
        this.nivelAccesoUsuarios=true;
      }
    },

    ocultarAccesosUsuarios(){
      this.nivelAccesoUsuarios = false;
    },


    selectOptionSolicitud(option){
      this.valueOptionSolicitudes=option;
    },

    showOptionsSolicitudes(){
      if(this.showSelectSolicitudes === true){
        this.showSelectSolicitudes=false;
      }else{
        this.showSelectSolicitudes=true;
      }
    },

    selectOptionPerfil(option){
      this.valueOptionPerfiles=option;
    },

    showOptionsPerfiles(){
      if(this.showSelectPerfiles === true){
        this.showSelectPerfiles=false;
      }else{
        this.showSelectPerfiles=true;
      }
    },

    selectOptionUsuario(option){
      this.valueOptionUsuarios=option;
    },

    showOptionsUsuarios(){
      if(this.showSelectUsuarios === true){
        this.showSelectUsuarios=false;
      }else{
        this.showSelectUsuarios=true;
      }
    },

    selectOptionFlujo(option){
      this.valueOptionFlujos=option;
    },

    showOptionsFlujo(){
      if(this.showSelectFlujos === true){
        this.showSelectFlujos=false;
      }else{
        this.showSelectFlujos=true;
      }
    },
  
    }
  }
  </script>