<template>
<div class="general">
<Slider texto="Pagina de pruebas"></Slider>
    <div class="center">
    <section id="content">
        <h2 class="subheader">Pagina de pruebas</h2>
        <h3>{{id_desde_url}}</h3>
        <button @click="actualizarNombre()">Actualizar Nombre</button>
        <button @click="redirigirAlblog()">Redirigir</button>
        <h4>{{nombre}}</h4>
    </section>
    <Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
</div>
</template>
<script>
import Slider from './Slider.vue'
import Sidebar from './Sidebar.vue'
export default {
    name: 'Pagina',
    components: {
    Slider,
    Sidebar
    },
    created(){
        // eslint-disable-next-line no-console
        console.log('componente creado');
    },
    mounted(){
        this.id_desde_url = this.$route.params.id;
        // eslint-disable-next-line no-console
        console.log('componente montado');
    },
    updated(){
        // eslint-disable-next-line no-console
        console.log('componente actualizado');
    },
    destroyed(){
        // eslint-disable-next-line no-console
        console.log('componente eliminado');
    },
    data(){
        return {
            id_desde_url: null,
            nombre: "deco"
        };

    },
    methods:{
        actualizarNombre(){
            this.nombre = "DECO";
        },
        redirigirAlblog(){
            this.$router.push('/blog');
        }
    }
};
</script>