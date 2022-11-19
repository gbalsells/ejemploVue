<template>
  <!-- <h1>Comentario</h1> -->
  <h1 @click="saludar">Primera página Vue</h1>
  <h2>Bienvenido, {{ nombreMayusculas }}</h2>
  <input type="text" v-model="nombre" @keydown.enter="saludar">
  <p>Nombre viejo: {{ nombreViejo }}</p>
  <select v-model="materiaFavorita">
    <option :value="materia" v-for="materia in materias">{{ materia }}</option>
  </select>
  <button @click="saludar">Saludar</button>
  <img :src="image">
  <p>La materia favorita de {{ nombre }} es: {{ materiaFavorita }}</p>
  <p>Carrera: {{ carrera }}</p>
  <p>Edad: {{ edad }}</p>
  <h3>{{ nombre }} es mayor de edad?: </h3>
  <p v-if="edad >= 18">Sí</p>
  <p v-else="edad < 18">No</p>
  <p v-for="materia in materiasFiltradas">{{ materia }}</p>
</template>

<script>
export default {
  name: 'HelloWorld',
  beforeCreate() {
    console.log('PROBANDO BEFORECREATE', this.nombre)
  },
  created() {
    console.log('PROBANDO CREATED', this.nombre)
    // fetch('url').then((r) => {
    //   this.nombre = r
    // })
  },
  mounted() {
    console.log('PROBANDO MOUNTED')
  },
  data() {
    //Ctrl + K + C => Comentar
    //Ctrl + K + U => Descomentar
    return {
      nombre: 'Guido Balsells', //comentario
      carrera: 'Ingeniería en Computación',
      edad: 27,
      materias: ['Programación II', 'Algebra II', 'Micro', 'Base de Datos'],
      materiaFavorita: '',
      image: '',
      nombreViejo: '',
    }
  },
  methods: {
    saludar() {
      let mensaje = 'Buenos días'
      alert(`${mensaje}: ${this.nombre}`)
    },
  },
  computed: {
    materiasFiltradas() {
      return this.materias.filter((materia) => materia.includes('II'))
    },
    nombreMayusculas() {
      return this.nombre.toUpperCase()
    }
  },
  watch: {
    nombre: function (newVal, oldVal) {
      this.nombreViejo = oldVal
    }
  },
}
</script>


<style scoped>
/**
Comentario
h1 {
  background-color: rebeccapurple;
}
*/
</style>
