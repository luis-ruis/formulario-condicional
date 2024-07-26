<template>
  <form>
    
    <div>
      <label>¿De qué país provienes?</label><br>
      <input type="radio" id="mexico" value="México" v-model="selectedCountry">
      <label for="mexico">México</label><br>
      <input type="radio" id="holanda" value="Holanda" v-model="selectedCountry">
      <label for="holanda">Holanda</label><br>
      <input type="radio" id="otro" value="Otro" v-model="selectedCountry">
      <label for="otro">Otro</label>
    </div>

    <!-- Pregunta condicional -->
    <div v-if="selectedCountry === 'Otro'">
      <label for="otherCountry">¿Cuál es el nombre de tu país?</label><br>
      <input type="text" id="otherCountry" v-model="otherCountry">
    </div>
  </form>
</template>

<script setup>
import { ref } from 'vue';

const selectedCountry = ref('');
const otherCountry = ref('');
</script>

<style scoped>

</style>
