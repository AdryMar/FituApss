<template>
  <v-app>
    <v-toolbar app class="menu">
      <v-spacer></v-spacer>
      <div class="container admin">
        <div class="row d-flex justify-content-end">
          <h5 class>Admin</h5>
        </div>
        <div class="row d-flex justify-content-end">
          <v-btn class="aqua" x-small>FituPets</v-btn>
        </div>
      </div>
    </v-toolbar>
    <v-toolbar app class="menu">
      <div class="container admin borall">
        <div class="row d-flex justify-content-start">
          <div class="col-md-4 allborder">
            <h5 class="All text-center">All</h5>
          </div>
        </div>
      </div>
    </v-toolbar>

    <v-navigation-drawer class="celeste" app v-model="drawer">
      <div class="container cabecera">
        <div class="row d-flex justify-content-center header">
          <img src="./assets/fitu.png" alt />
        </div>

        <div class="row margin-top padding-left">
          <router-link to="/" exact class="icon">
            <i class="fas fa-dog mr-2"></i> Pets
          </router-link>
        </div>

        <div class="row d-flex justify-content-center padding-righ">
          <router-link to="/agregar" class="icon">
            <i class="fas fa-paw mr-2"></i> Add Pets
          </router-link>
        </div>
      </div>
    </v-navigation-drawer>

    <v-content class="cuerp-petts">
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data() {
    return {
      drawer: true
    };
  }
};
</script>

<style >
.cuerp-petts {
  background: #f5f6fa;
}
.borall {
  padding-left: 60px;
  padding-bottom: 0px !important;
}
.All {
  color: #0062b7 !important;
}
.allborder {
  border-bottom: 5px solid #0062b7;
}
.admin {
  padding-right: 150px !important;
}
.admin h5 {
  font-weight: bold;
}
.aqua {
  background: #00d1b2 !important;
  color: white !important;
  text-transform: capitalize !important;
  font-size: 0.5rem !important;
}
.header {
  background: #0062b7 !important;
  padding: 5px 0px;
}
.cabecera {
  padding: 0px !important;
}
.celeste {
  background: #006ecd !important;
}
.margin-top {
  padding-top: 90px;
}
.a.router-link-exact-active {
  color: rgb(0, 187, 162) !important;
  border-top: 3px solid blue;
  border-bottom: 3px solid blue;
}
.padding-left {
  padding: 90px 95px 10px 95px;
}
.padding-righ {
  padding: 5px 0px 0px 1px;
}
.icon {
  color: white !important;
  font-weight: bold !important;
}
</style>