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
              <form >

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

export default {
  name: 'App',
  components: {
  }
}
</script>

<style>

</style>
