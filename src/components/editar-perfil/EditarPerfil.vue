<template>
  <div 
    id="modalEditarPerfil"
    :class="modalEditarPerfil"
  >
    <div modal-form>
      <div class="contenido-modal">
        <div class="contenido-modal-child">
          <h4 style="margin-bottom: 30px; text-align: left;">
            <b> Editar perfil</b>
          </h4>
          <div
            class="form-group row"
            style="margin-bottom: 70px;"
          >
            <div class="col-sm-6">
              <input
                id="nombrePerfil"
                v-model="nombrePerfil"
                placeholder="Promotor BE"
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
          <div class="div-buttons">
            <button
              class="button-cancel-changes"
              @click="closeEditarPerfil()"
            >
              Cancelar
            </button>
            <button
              class="button-save-changes-edit"
              @click="saveChangesPerfil()"
            >
              Guardar cambios
            </button>
          </div>
        </div>
        <span
          class="closeModal"
          @click="closeEditarPerfil()"
        >&times;</span>
      </div>
    </div>
  </div>
</template>
<script>
import '@/publico/css/editar-perfil/editar-perfil.css'
export default {
    name:'EditarPerfil',
    props:{
        dataUser:{
            type:Object
        },
    },
    data(){
        return{
            modalEditarPerfil:'close-modal-editar-perfil',
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
    created(){
    },
    methods:{
        openEditarPerfil(){
            this.modalEditarPerfil='open-modal-editar-perfil';
            console.log("si abre")
        },
        closeEditarPerfil(){
            this.modalEditarPerfil='close-modal-editar-perfil';
        },

        saveChangesPerfil(){
            this.closeEditarPerfil();
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