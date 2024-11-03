<template>
    <div class="card mb-3" :style="{ backgroundColor: colorFondo }">
    <div class="card-body">
        <h5 class="card-title">{{ cita.paciente }}</h5>
        <p class="card-text"><strong>Fecha:</strong> {{ cita.fecha }}</p>
        <p class="card-text"><strong>Hora:</strong> {{ cita.hora }}</p>
        <p class="card-text"><strong>Gravedad:</strong> {{ cita.gravedad }}</p>
        <p class="card-text"><strong>Motivo:</strong> {{ cita.motivo }}</p>
        <button class="btn btn-danger" @click="eliminarCita">Eliminar</button>
    </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CitaCard',
    props: {
      cita: Object
    },
    computed: {
      colorFondo() {
        switch (this.cita.gravedad) {
          case 'baja':
            return 'green';
          case 'media':
            return 'yellow';
          case 'alta':
            return 'red';
          default:
            return 'white';
        }
      }
    },
    methods: {
      eliminarCita() {
        this.$emit('eliminarCita');
      }
    }
  };
  </script>
  
  <style scoped>
  .card {
    border: 1px solid #ccc;
  }
  </style>