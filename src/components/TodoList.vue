<template>
<div class="alumno-list">
  <h1>{{alumnos.length}} Alumnos</h1>
  <form class="form" @submit.prevent="createAlumno">
    <label class="label" for="alumno">Nuevo Alumno: </label>
    <input class="input" type="text" v-model="nuevoAlumno" id="alumno" />
    {{ nuevoAlumno }}
    <input class="button" type="submit" value="Crear alumno" />
    </form>
    <ul class="list">
      <input type="submit" value="Marcar o Desmarcar a Todos los alumnos" @click="marcarDesmarcarAlumnos()" />
      <li class="alumno"
        v-for="(alumno, i) in alumnos"
        :key="'alumno' + i"    
        :class="{ completed: alumno.completed }"
        @click="completeAlumno(alumno.text)"
      >
        {{ alumno.text }}
        <!--<input type="submit" value="Eliminar alumno" @click="deleteAlumno(alumnos.indexOf(alumno.text))"/>-->
        <input type="submit" value="Eliminar alumno" @click="deleteAlumno(i)"/>       

      </li>
    </ul>
  
</div>
</template>

<script>
export default {
  data: () => ({
    nuevoAlumno: "",
    alumnos: [],
  }),
  methods: {
    createAlumno() {
      let alumno = {
        text: this.nuevoAlumno,
        completed: true,
      };
      this.alumnos.push(alumno);
      this.nuevoAlumno = "";
      console.log(this.alumnos);
    },
    completeAlumno(alumnoText) {
      for (let i = 0; i < this.alumnos.length; i++) {
        let alumno = this.alumnos[i];
        if (alumnoText === alumno.text) {
          alumno.completed = !alumno.completed;
        }
      }
    },
    deleteAlumno(i) {
      this.alumnos.splice(i,1);
    },
    marcarDesmarcarAlumnos() {
      for (let i = 0; i < this.alumnos.length; i++) {
        let alumno = this.alumnos[i];
        alumno.completed = !alumno.completed;
      }
    }
  },
};
</script>

<style scoped>
.alumno-list {
  width: 800px;
  max-width: 100%;
  margin: 0px auto;
}
.form {
  background: white;
  border-radius: 12px;
  padding: 30px;
  box-shadow: 0px 10px 22px -1px rgba(0,0,0,0.25);
  margin-top: 10px;
}
.label {
  display: block;
  margin-bottom: 10px;
}
.input {
  height: 35px;
}
.button {
  margin-left: 20px;
  height: 35px;
  border: none;
  border-radius: 5px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, .2);
  background-color: #2ecc71;
  color: #ecf0f1;
  cursor: pointer
}
.list {
  margin-top: 40px;
}
.alumno {
  cursor: pointer;
  margin: 10px 0;
}
.completed {
  text-decoration: line-through;
  color: lightgrey;
}
</style>