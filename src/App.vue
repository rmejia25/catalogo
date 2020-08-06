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
                    <tr v-for="w in websites" :key="w.value">
                      <td>
                        <a v-bind:href="w.url" target="_blank">{{w.nombre}}</a>
                      </td>
                      <td>
                        {{w.autor}}
                      </td>
                      <td>
                        <button class="btn btn-danger">Eliminar</button>
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

export default {
  name: 'App',
  firebase:{
    websites: websitesRef
  },

  data(){
    return{
      newWebsite:{
        nombre: '',
        autor: '',
        url: ''
      }
    }
  },
  methods:{
    addWebite(){
      websitesRef.push(this.newWebsite);
      this.newWebsite.nombre = '';
      this.newWebsite.autor = '';
      this.newWebsite.url = '';
    }

  }
}
</script>

<style>

</style>
