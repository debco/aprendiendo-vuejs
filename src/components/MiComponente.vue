<template>
    <div id="mi-componente ">
        <h1>Es es mi componente</h1>
        <h2>{{subtitulo}}</h2>
    </div>
</template>
<script>
export default {
    name: "MiComponente",
    data(){
        return{
            subtitulo: "soy el subtitulo de de mi componente"
        }
    }
}
</script>