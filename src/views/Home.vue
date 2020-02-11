<template>
  <div class="home">
    <div class="container">
      <div class="row">
        <h1 class="pets">Pets</h1>
      </div>

      <div class="row">
        <div class="card" style="width: 100%;">
          <table class="table table-hover">
            <thead class="thime">
              <tr>
                <th scope="col" class="tema">ID</th>
                <th scope="col" class="tema">Name</th>
                <th scope="col" class="tema">Type</th>
                <th scope="col" class="tema">Color</th>

                <th scope="col" class="tema">Breed</th>
                <th scope="col" class="tema">Gender</th>
                <th scope="col" class="tema">Age</th>
                <th scope="col" class="tema">Created at</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(item, index) in mascotas" :key="index">
                <th scope="row">{{item.id}}</th>
                <td>{{item.name}}</td>
                <td>{{item.kind}}</td>
                <td>gggg</td>
                <td>Mark</td>
                <td>Otto</td>
                <td>@mdo</td>
                <td>{{item.created_at}}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      mascotas: [],
      mascota: { name: "", kind: "" }
    };
  },
  created() {
    this.listarMascotas();
  },
  methods: {
    listarMascotas() {
      this.axios
        .get("?token=56437ee14d804bfa14762e0b1782827e")
        .then(res => {
          console.log(res.data);
          this.mascotas = res.data;
        })
        .catch(error => {
          console.log(error);
        });
    },
    agregarMascota() {
      console.log(this.mascota);
      this.axios
        .post("?token=56437ee14d804bfa14762e0b1782827e", this.mascota)
        .then(res => {
          this.mascotas.push(res.data);
          this.mascota.name = "";
          this.mascota.kind = "";
        })
        .catch(error => {
          console.log(error);
        });
    }
  },

  components: {}
};
</script>

<style >
.tema {
  font-weight: bold;
  color: #023e57;
}
.pets {
  font-weight: bold;
  color: #023e57;
  padding: 60px 0px;
}
.thime {
  padding: 20px 0px !important;
}
</style>