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
              <form >g

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
import config from './config';

let app = Firebase.initializeApp(config);
let db = app.database();
let websiteRef = db.ref('websites');

export default {
  name: 'App',
  firebase:{
    websites: websiteRef
  },

  data(){

    return{
      newWebsite:{
        nombre: '',
        autor: '',
        url: ''
      }
    }
  }
}
</script>

<style>

</style>
