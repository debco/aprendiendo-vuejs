<template>
  <div class="general">
    <div class="center">
      <section id="content">
        <h1 class="subheader">Peliculas</h1>
        <div class="favorita" v-if="favorita">
            <h2>{{favorita.title}}</h2>
        </div>
        <!--Listado articulos-->
        <div id="articles">
          <div v-for="pelicula in peliculasMayuscula" v-bind:key="pelicula.title">
            <Pelicula
              :pelicula="pelicula"
              @favorita="haLlegadoLaPeliculaFavorita"
            ></Pelicula>
          </div>
          <!--v-for="pelicula in peliculas" v-bind:key="pelicula.title"-->
        </div>
      </section>
      <Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
  </div>
</template>
<script>
import Pelicula from "./Pelicula.vue";
import Sidebar from "./Sidebar.vue";
export default {
  name: "Peliculas",
  components: {
    Pelicula,
    Sidebar
  },
  methods: {
    haLlegadoLaPeliculaFavorita(favorita) {
      this.favorita = favorita;
    }
  },
  filters:{
      mayusculas(value){
          return value.toUpperCase();
      }
  },
  computed: {
      peliculasMayuscula(){
          var peliculasMod = this.peliculas;
          for(var i= 0; i < this.peliculas.length; i++){
              peliculasMod[i].title = peliculasMod[i].title.toUpperCase();
          }
          return peliculasMod;
      }
  },
  data() {
    return {
      favorita: null,
      peliculas: [
        {
          title: "Batman vs Superman",
          year: 2003,
          image: "https://www.moviezone.cz/obr/YXJ0aWNsZU1haW4vMTg2NjA2"
        },
        {
          title: "deadpool",
          year: 2018,
          image:
            "https://depor.com/resizer/_IzpcKdVES0XRfdZKhHNo9xsalY=/980x528/smart/arc-anglerfish-arc2-prod-elcomercio.s3.amazonaws.com/public/I7OH6CTB3JFGZNLNXWPPUH2FHI.jpg"
        },
        {
          title: "Stranger Things",
          year: 2015,
          image:
            "https://culto.latercera.com/wp-content/uploads/2019/07/stranger-things-3-900x600.jpg"
        }
      ]
    };
  }
};
</script>
