<template>
    <section id="content">
        <h2 class="subheader">{{titulo}}</h2>
        <h1>Es es mi componente</h1>
        <h2>{{subtitulo}}</h2>

        <h2>reactividad</h2>
        <input type="text" v-model="nombre"/>
        mi nombre es <strong>{{nombre}}</strong>
        <!--<pre>
            {{$data}}
        </pre>-->
        <h2>directivas condicionales</h2>
        <input type="number" v-model="edad"/>
        mi edad es <strong>{{edad}}</strong>

        <p style="color:red;" v-if="edad && edad >=18 && edad <=65">
          eres mayor de edad
        </p>

        <p style="color:purple;" v-else-if="edad && edad > 65">
          eres adulto mayor de edad
        </p>

        <!--<p style="color:green;" v-if="edad && edad < 18">-->
        <p style="color:green;" v-else>
          eres menor de edad
        </p>

        <h2>directivas iterativa</h2>
        <ol>
           <li v-for="pelicula in peliculas" :key="pelicula">
               {{pelicula}}
            </li> 
        </ol>

    </section>
</template>
<script>
export default {
    name: "MiComponente",
    data(){
        return{
            titulo: "mi componente",
            subtitulo: "soy el subtitulo de de mi componente",
            nombre:'',
            edad:18,
            peliculas: ['batman vs superman', 'el señor de los anillos', 'spiderman','aventura']
        }
    }
}
</script>