<template>
  
  <div>
    <Candidato :foto="fot" :nombre="nombre1" :apellido="apellido1" :ciudad="ciudad1" :pais="pais1" />
    
    
      <label>Foto:</label>
      <input type="text" v-model="fot" readonly />
    </div>
    <div>
      <label>Nombre:</label>
      <input type="text" v-model="nombre1" />
    </div>
    <div>
      <label>Apellido:</label>
      <input type="text" v-model="apellido1" />
    </div>
    <div>
      <label>Ciudad:</label>
      <input type="text" v-model="ciudad1" />
    </div>
    <div>
      <label>Pais:</label>
      <input type="text" v-model="pais1" />
    </div>
  
  <button @click="mostrar()">BUSCAR</button>
  <button @click="agregar()">AGREGAR</button>

</template>

<script>
import Candidato from './components/Candidato.vue'

export default {
  name: 'App',
  components: {
    Candidato,
  },
  data() {
    return {
      fot: '',
      nombre1: '',
      apellido1: '',
      ciudad1: '',
      pais1: ''
    };
  },
  methods: {
    async mostrar() {
      const id = 0;
      const data = await this.cargarAPI(id);
      this.fot = data.results[id].picture.large;
      this.nombre1 = data.results[id].name.first;
      this.apellido1 = data.results[id].name.last;
      this.ciudad1 = data.results[id].location.city;
      this.pais1 = data.results[id].location.country;
    },
    async cargarAPI(id) {
      const url = 'https://randomuser.me/api/';
      const respuesta = await fetch(url);
      const data = await respuesta.json();
      return data;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
