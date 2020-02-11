<template>
  <div class="home">
    <div class="container">
      <div class="row">
        <h1 class="pets">Pets</h1>
      </div>

      <div class="row">
        <form @submit.prevent="agregarMascota()" style="width: 100%;">
          <h3>Agregar Pets</h3>
          <div class="form-row">
            <div class="col">
              <input
                type="text"
                class="form-control my-2"
                placeholder="Nombre"
                v-model="mascota.name"
              />
            </div>
            <div class="col">
              <input
                type="text"
                class="form-control my-2"
                placeholder="Type"
                v-model="mascota.kind"
              />
            </div>
          </div>
          <div class="form-row">
            <div class="col">
              <input type="text" class="form-control" placeholder="Color" v-model="mascota.color" />
            </div>
            <div class="col">
              <input type="text" class="form-control" placeholder="Breed" v-model="mascota.breed" />
            </div>
          </div>
          <div class="form-row">
            <div class="col">
              <input type="text" class="form-control" placeholder="Gender" v-model="mascota.gender" />
            </div>
            <div class="col">
              <input type="number" class="form-control" placeholder="Age" v-model="mascota.age" />
            </div>
          </div>
          <button type="submit" class="btn-success btn btn-block mb-4">Agregar</button>
        </form>
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
                <td>{{item.color}}</td>
                <td>{{item.breed}}</td>
                <td>{{item.gender}}</td>
                <td>{{item.age}}</td>
                <td>{{item.created_at}}</td>
                <td>
                  <button class="btn" @click="eliminarMascota(item.id)">Eliminar</button>
                </td>
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
      mascota: { name: "", kind: "", color: "", breed: "", gender: "", age: 0 }
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
          this.mascota.color = "";
          this.mascota.breed = "";
          this.mascota.gender = "";
          this.mascota.age = "";
        })
        .catch(error => {
          console.log(error);
        });
    },
    eliminarMascota(id) {
      console.log(id);
      this.axios
        .delete(`?token=56437ee14d804bfa14762e0b1782827e/${id} `)
        .then(res => {
          const index = this.mascotas.findIndex(item => item.id === res.data);
          this.mascotas.splice(index, 1);
        })
        .catch(err => {
          console.log(err);
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