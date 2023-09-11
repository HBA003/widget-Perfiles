<template>
  <div
    v-if="mostrarTarjeta === id_perfil"
    class="card card-acciones no-border"
    style="width: 10rem;"
  >
    <div
      class="card-body tarjeta-wrapper tarjeta-body"
    >
      <p class="card-title titulo">
        <strong>ACCIONES</strong>
      </p>
      <ul>
        <img
          src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/b18373ed-2e9b-4530-b1a3-2d4c98e31011/original/Icons_Blue-_buttons_outline.svg"
          alt=""
        >        <a
          href="#"
          class="card-link tarjeta-link"
          @click="openEditarPerfil()"
        ><strong>EDITAR</strong></a>
      </ul>  
      <hr class="linea-acciones">
      <ul class="ul-desact">
        <img
          src="https://d2ra1qv4p9we6t.cloudfront.net/uploads/e3e74596-cc09-46cf-b815-b5a179ff91c4/original/Vector_1_.svg"
          alt=""
        >
        <a
          href="#"
          class="card-link tarjeta-link"
          @click="openDesactivarPerfil()"
        ><strong>DESACTIVAR</strong></a>
      </ul>
    </div>
    <editar-perfil
      ref="editarPerfilRef"
      :data-user="dataUser"
    />
    <desactivar-perfil 
      ref="desactivarPerfilRef"
      :data-user="dataUser"
    />
  </div>
</template>

<script>
  import '@/publico/css/acciones-perfil/acciones-perfil.css';
  import EditarPerfil from '../editar-perfil/EditarPerfil.vue';
  import DesactivarPerfil from '../desactivar-perfil/DesactivarPerfil.vue';
  export default {
    name: 'AccionesPerfil',
    components:{
      EditarPerfil,
      DesactivarPerfil
    },
    props:{
      mostrarTarjeta:{
        type: Number,
        default: 0
      },
      id_perfil:{
        type:Number,
        default:0
      },
      dataUser:Object
    },
    data(){
      return{
        openEditPerfil:false,
        openDesactPerfil:false,
      }
    },
    methods:{
      openEditarPerfil(){
        this.$refs.editarPerfilRef.openEditarPerfil();
        console.log("abriendo editar perfil")
      },
      openDesactivarPerfil(){
        this.$refs.desactivarPerfilRef.openDesactivarPerfil();
      }
    }
  }
</script>