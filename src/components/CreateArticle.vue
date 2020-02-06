<template src="./CreateArticle.html"></template>

<script>
import Sidebar from "./Sidebar.vue";
import Global from "../Global";
import Article from "../models/Article";
import axios from "axios";
import { requerid } from "vuelidate/lib/validators";
import swal from "sweetalert";

export default {
  name: "CreateArticle",
  components: {
    Sidebar
  },
  data() {
    return {
      file: "",
      url: Global.url,
      article: new Article("", "", null, ""),
      submitted: false
    };
  },
  validations: {
    article: {
      title: {
        requerid
      },
      content: {
        requerid
      }
    }
  },
  mounted() {
    //console.log(this.article);
  },
  methods: {
    fileChange() {
      this.file = this.$refs.file.files[0];
      //console.log(this.file);
    },
    save() {
      this.submitted = true;
      /*this.$v.$touch();
      if(this.$v.$invalid){
        return false;
      }else{*/
      axios
        .post(this.url + "save", this.article)
        .then(response => {
          if (response.data.status == "success") {
            // subida de archivo
            if (
              this.file != null &&
              this.file != undefined &&
              this.file != ""
            ) {
              const formData = new FormData();
              formData.append("file0", this.file, this.file.name);
              var articleId = response.data.article._id;

              axios
                .post(this.url + "upload-image/" + articleId, formData)
                .then(response => {
                  if (response.data.article) {
                    swal(
                      "Articulo creado",
                      "El articulo se ha creado con exito :) ",
                      "success"
                    );
                    this.article = response.data.article;
                    this.$router.push("/blog");
                  } else {
                    swal(
                      "Articulo no se ha creado bien",
                      "creacion fallido",
                      "error"
                    );
                  }
                })
                .catch(error => {
                  console.log(error);
                });
            } else {
              swal(
                "Articulo creado sin imagen",
                "El articulo se ha creado con exito :) ",
                "success"
              );
              this.article = response.data.article;
              this.$router.push("/blog");
            }
          }
        })
        .catch(error => {
          console.log(error);
        });
      //}
    }
  }
};
</script>
