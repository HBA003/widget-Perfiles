<template>
  <div
    :class="modalDesactivar"
  > 
    <div modal-form>
      <div class="contenido-modal-exportar">
        <div class="contenido-modal-child">
          <h4
            style="margin-bottom: 30px; text-align: left;"
          >
            <b>Desactivar Perfil</b>
          </h4>
          <h6
            style="text-align: left;"
          >
            Se desactivará el perfil. ¿Desea continuar?
          </h6>
          <div class="div-buttons">
            <button
              class="button-cancel-changes"
              @click="closeModalDesactivar()"
            >
              Cancelar
            </button>
            <button
              class="button-save-changes"
              @click="saveChangesPerfil()"
            >
              Continuar
            </button>
          </div>
        </div>
        <span
          class="closeModal"
          @click="closeModalDesactivar()"
        >&times;</span>
      </div>
    </div>
  </div>
</template>
<script>
import '@/publico/css/desactivar-perfil/desactivar-perfil.css'
export default {
    name: 'DesactivarPerfil',
    props:{
      dataUser:{
        type:Object
      },
    },
    data(){
      return{
        modalDesactivar:'close-modal-cancelar-solicitud',
      }
    },
    methods :{
      openDesactivarPerfil(){
        this.modalDesactivar='open-modal-cancelar-solicitud';
        

       },
       closeModalDesactivar(){
         this.modalDesactivar='close-modal-cancelar-solicitud';
       },

       saveChangesPerfil(){
        //alert("Guardando cambios en la api")
        this.closeModalDesactivar();
       }

    
    }
}
</script>