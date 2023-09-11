<template>
  <div
    v-if="mostrarCard"
    class="card tarjeta-exportar"
  >
    <table class="table tarj-body">
      <tbody>
        <tr>
          <td>
            <button
              class="btn-archivo"
              @click="openExportar('XLS')"
            >
              XLS
            </button>
          </td>
        </tr>
        <tr>
          <td>
            <button
              class="btn-archivo"
              @click="openExportar('CSV')"
            >
              CSV
            </button>
          </td>
        </tr>
        <tr>
          <td>
            <button
              class="btn-archivo"
              @click="openExportar('TXT')"
            >
              TXT
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <div
      :class="modalExportar"
    > 
      <div modal-form>
        <div class="contenido-modal-exportar">
          <div class="contenido-modal-child">
            <h4
              style="margin-bottom: 30px; text-align: left;"
            >
              <b>Exportar Perfiles</b>
            </h4>
            <h6
              style="text-align: left;"
            >
              Se exportarán todos los registros existentes. ¿Deseas continuar?
            </h6>
            <div class="div-buttons-export">
              <button
                class="button-cancel-changes"
                @click="closeExportarPerfiles()"
              >
                Cancelar
              </button>
              <button
                class="button-save-changes"
                @click="saveChangesPerfiles()"
              >
                Continuar
              </button>
            </div>
          </div>
          <span
            class="closeModal"
            @click="closeExportarPerfiles()"
          >&times;</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import '@/publico/css/exportar-tabla/exportar-tabla.css'
export default {
  name: 'ExportarTabla',
  props:{
    mostrarCard:Boolean
  },
  data() {
    return {
      modalExportar:'close-modal-exportar-perfil',
      formatoExportacion:'',
    }
  },
  methods:{
    openExportar(formato) {
      this.formatoExportacion = formato;
      this.modalExportar = 'open-modal-exportar-perfil'
    },

    closeExportarPerfiles(){
      this.modalExportar='close-modal-exportar-perfil';
      this.formatoExportacion = '';
    },

    saveChangesPerfiles(){
      this.closeExportarPerfiles();
    }
  }
  
}
</script>