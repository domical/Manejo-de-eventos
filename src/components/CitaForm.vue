<template>
    <form @submit.prevent="submitForm">
      <div class="mb-3">
        <label :class="{ 'text-danger': !paciente }">Paciente</label>
        <input type="text" v-model="paciente" @input="validarCampos" class="form-control" />
      </div>
      
      <div class="mb-3">
        <label :class="{ 'text-danger': !fecha }">Fecha</label>
        <input type="date" v-model="fecha" @input="validarCampos" class="form-control" />
      </div>
      
      <div class="mb-3">
        <label :class="{ 'text-danger': !hora }">Hora</label>
        <input type="time" v-model="hora" @input="validarCampos" class="form-control" />
      </div>
      
      <div class="mb-3">
        <label :class="{ 'text-danger': !gravedad }">Gravedad</label>
        <select v-model="gravedad" @input="validarCampos" class="form-control">
          <option value="" disabled selected>Selecciona gravedad</option>
          <option value="baja">Baja</option>
          <option value="media">Media</option>
          <option value="alta">Alta</option>
        </select>
      </div>
      
      <div class="mb-3">
        <label :class="{ 'text-danger': !motivo }">Motivo</label>
        <textarea v-model="motivo" @input="validarCampos" class="form-control"></textarea>
      </div>
      
      <button type="submit" class="btn btn-primary" :disabled="!formCompleto">Agregar</button>
    </form>
  </template>
  
  <script>
  export default {
    name: 'CitaForm',
    data() {
      return {
        paciente: '',
        fecha: '',
        hora: '',
        gravedad: '',
        motivo: '',
        formCompleto: false,
      };
    },
    methods: {
      validarCampos() {
        this.formCompleto = this.paciente && this.fecha && this.hora && this.gravedad && this.motivo;
      },
      submitForm() {
        const nuevaCita = {
          paciente: this.paciente,
          fecha: this.fecha,
          hora: this.hora,
          gravedad: this.gravedad,
          motivo: this.motivo
        };
        this.$emit('agregarCita', nuevaCita);
        this.limpiarFormulario();
      },
      limpiarFormulario() {
        this.paciente = '';
        this.fecha = '';
        this.hora = '';
        this.gravedad = '';
        this.motivo = '';
        this.formCompleto = false;
      }
    }
  };
  </script>
  
  <style scoped>
  .text-danger {
    color: red;
  }
  </style>