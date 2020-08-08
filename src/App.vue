<template>
  <div id="app">
    <nav class="navbar navbar-dark bg-primary">
      <a href="/" class="navbar-brand">Vuejs Firebase Database</a>
    </nav>
    <!--MAIN CONTENT-->
    <div class="container">
      <div class="row mt-5">
        <div class="col-sm-4">
          <div class="card">
            <div class="card-header">
              <h3>Agrega nuevo sitio web</h3>

            </div>
            <div class="card-body">
              <form @submit.prevent="addWebite">
                <div class="form-group">
                  <input type="text" name="" id="" class="form-control" v-model="newWebsite.nombre"
                  placeholder="Nombre">                
                </div>

                <div class="form-group">
                  <input type="text" name="" id="" class="form-control" v-model="newWebsite.autor"
                  placeholder="Autor">                
                </div>

              <div class="form-group">
                  <input type="text" name="" id="" class="form-control" v-model="newWebsite.url"
                  placeholder="Url">                
                </div>

                <button type="submit" class="btn btn-primary">
                  Guardar
                </button>

              </form>

            </div>
          </div>

        </div>
        <div class="col-sm-8 text-center">
            <img alt="Vue logo" src="./assets/logo.png">
            <div class="card">
              <div class="card-header">
                <h3>Lista de sitios web</h3>

              </div>
              <div class="card-body">
                <table class="table table-striped table-bordered">
                  <thead>
                    <tr>
                      <th>Nombre</th>
                      <th>Autor</th>
                      <th>Operaciones</th>
                    </tr>

                  </thead>
                  <tbody>
                    <tr v-for="w in websites" v-bind:key="w.website">
                      <td>                        
                        <a v-bind:href="w.url" target="_blank">{{w.nombre}}</a>
                      </td>
                      <td>
                        {{w.autor}}
                      </td>
                      <td>
                         <button @click="deleteWebsite(w)" class="btn btn-danger">Eliminar</button>
                      </td>

                    </tr>

                  </tbody>
                </table>
              </div>
            </div>

        </div>

      </div>

    </div>
  </div>
</template>

<script>
import Firebase from 'firebase';
import config from './config.js';

let app = Firebase.initializeApp(config);
let db = app.database();
let websitesRef = db.ref('websites');

import toastr from 'toastr';

export default {
  name: 'App',
  firebase:{
    websites: websitesRef
  },

  data(){
    return{
      websites:[],
      newWebsite:{
        nombre: '',
        autor: '',
        url: ''
      }
    }
  },

created() {
             Firebase.database().ref('websites').on('value', (snapshot) => {
                 this.websites = snapshot.val() 
             })
         }, 

  methods:{
    addWebite(){
      websitesRef.push(this.newWebsite);
      toastr.success('Sitio Web Agregado');

      this.newWebsite.nombre = '';
      this.newWebsite.autor = '';
      this.newWebsite.url = '';
      
    },
    deleteWebsite:function(w){
       if(confirm('Are you sure delete it?')) {
         //Firebase.database().ref("websites").child(id).remove();
         websitesRef.child(w['.key']).remove();
      toastr.success('Website removed');
       }
    }

  }
}
</script>

<style>

</style>
