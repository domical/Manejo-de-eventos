<template>
  <div class="container my-5">
    <h1>Administrador de Citas Médicas</h1>
    <CitaForm @agregarCita="agregarCita" />
    
    <div v-if="citas.length === 0" class="alert alert-warning">
      Aún no hay consultas registradas.
    </div>
    
    <div class="row">
      <CitaCard 
        v-for="(cita, index) in citas" 
        :key="index" 
        :cita="cita" 
        @eliminarCita="eliminarCita(index)"
      />
    </div>
  </div>
</template>

<script>
import CitaForm from './components/CitaForm.vue';
import CitaCard from './components/CitaCard.vue';

export default {
  name: 'App',
  components: {
    CitaForm,
    CitaCard
  },
  data() {
    return {
      citas: []
    };
  },
  methods: {
    agregarCita(nuevaCita) {
      this.citas.push(nuevaCita);
    },
    eliminarCita(index) {
      this.citas.splice(index, 1);
    }
  }
};
</script>

<style>
.container {
  max-width: 600px;
  margin: auto;
}
</style>
