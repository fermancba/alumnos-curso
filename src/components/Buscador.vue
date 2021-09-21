<template>
  <div>
    <form @submit.prevent="buscar">
      <label class="label" for="alumno">Buscar alumno: </label>
      <input class="input" type="text" v-model="textoAlumno" id="alumno" />
      {{ textoAlumno }}
      <input class="button" type="submit" value="Buscar alumno" />
      <span>Alumno encontrado: {{alumnoEncontrado}}</span>
    </form>
  </div>
</template>

<script>
export default {
    data: () => ( {
        textoAlumno: "",
        alumnos: [],
        alumnoEncontrado: ""     
    }),
    methods: {
        buscar() {
            let alumno = this.alumnos.find(this.textoAlumno);    
            this.alumnos = alumno;  
            return this.alumnoEncontrado = alumno
        }
    }
}
</script>

<style scoped>
</style>
