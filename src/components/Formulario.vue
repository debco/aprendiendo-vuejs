<template>
  <div class="general">
    <div class="center">
      <section id="content">
        <h2 class="subheader">Formulario</h2>
        <form class="mid-form" @submit.prevent="mostrarUsuario()">
          <div class="form-group">
            <label for="nombre">Nombre</label>
            <input type="text" name="nombre" v-model="user.nombre" />
            <div v-if="submitted && !$v.user.nombre.required">este campo es obligatorio</div>
            <div v-if="submitted && !$v.user.nombre.minLength">este campo requiere 2 caracteres</div>
          </div>

          <div class="form-group">
            <label for="apellidos">Apellidos</label>
            <input type="text" name="apellidos" v-model="user.apellidos" />
            <div v-if="submitted && !$v.user.apellidos.required">este campo es obligatorio</div>
            <div v-if="submitted && !$v.user.apellidos.minLength">este campo requiere 2 caracteres</div>
          </div>

          <div class="form-group">
            <label for="bio">Biografia</label>
            <textarea name="bio" v-model="user.bio"></textarea>
            <div v-if="submitted && !$v.user.bio.required">este campo es obligatorio</div>
            <div v-if="submitted && !$v.user.bio.minLength">este campo requiere 10 caracteres</div>
          </div>

          <div class="form-group radibuttons">
            <input type="radio" name="genero" value="hombre" checked v-model="user.genero" />
            Hombre
            <input type="radio" name="genero" value="mujer" v-model="user.genero" />
            Mujer
          </div>

          <div class="clearfix"></div>

          <input type="submit" value="Enviar" class="btn btn-success" />
        </form>
        <div class="datos" v-if="user.nombre && user.apellidos">
          <h3>{{user.nombre + '' + user.apellidos}}</h3>
        </div>
      </section>
      <Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
  </div>
</template>
<script>
import { required, minLength } from "vuelidate/lib/validators";

import Sidebar from "./Sidebar.vue";
export default {
  name: "Formulario",
  components: {
    Sidebar
  },
  validations:{
    user:{
      nombre:{
      required,
      minLength: minLength(2)
    },
    apellidos:{
      required,
      minLength: minLength(2)
    },
    bio:{
      required,
      minLength: minLength(10)
    }
    }
    
  },
  data() {
    return {
      submitted: false,
      user: {
        nombre: "",
        apellidos: "",
        bio: "",
        genero: ""
      }
    };
  },
  methods: {
    mostrarUsuario() {
      // eslint-disable-next-line no-undef
      //console.log(this.user);
      this.submitted = true;

      this.$v.$touch();

      if(this.$v.$invalid){
        return false;
      }
      alert('validacion pasada');
    }
  }
};
</script>
