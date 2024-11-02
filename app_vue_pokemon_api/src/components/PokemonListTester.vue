<template>
    <div class="pokemon-list-tester">
      <button @click="toggleVisibility" class="btn btn-info mb-2">
        {{ isVisible ? 'Ocultar Nombres Correctos' : 'Mostrar Nombres Correctos' }}
      </button>
      <pre v-if="isVisible">{{ correctAnswers }}</pre>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      correctAnswers: {
        type: Array,
        required: true
      }
    },
    data() {
      return {
        isVisible: false
      };
    },
    methods: {
      toggleVisibility() {
        this.isVisible = !this.isVisible;
      }
    }
  };
  </script>
  
  <style scoped>
  pre {
    background-color: #f8f9fa;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    max-height: 300px;
    overflow-y: auto;
  }
  </style>
  