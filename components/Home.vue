<template>
  <div>
    <div>
      <form @submit.prevent="postData" class="pt-3" action="post">
        <b-container>
          <b-row>
            <!-- First column -->
            <b-col cols="12" sm="6">
              <!-- Nombre -->
              <div>
                <label class="text" for="name"> Nombre: </label>
                <input
                  type="text"
                  id="name"
                  placeholder="John"
                  required
                  class="box"
                  v-model="name"
                />
              </div>
              <!-- Genero -->
              <div>
                <label for="genero" style="padding-right: 6px;"> Genero: </label>
                <select class="box" name="genero" id="genero" required v-model="genero">
                  <option value="">None</option>
                  <option value="Hombre">Mujer</option>
                  <option value="Mujer">Hombre</option>
                </select>
              </div>
              <!-- País -->
              <div>
                <label for="pais" style="padding-right: 30px;"> País: </label>
                <select class="box" name="" id="pais" required v-model="pais">
                  <option value="">None</option>
                  <option value="México">México</option>
                  <option value="USA">USA</option>
                  <option value="Canada">Canada</option>
                </select>
              </div>
            </b-col>

            <!-- Second column -->
            <b-col cols="12" sm="6">
              <!-- Edad -->
              <div>
                <label for="edad" style="padding-right: 33px;">Edad:</label>
                <input
                  type="number"
                  id="edad"
                  placeholder="25"
                  min="18"
                  max="120"
                  required
                  class="box"
                  v-model="edad"
                />
              </div>
              <!-- Dirección -->
              <div>
                <label for="direccion">Dirección:</label>
                <input
                  type="text"
                  id="direccion"
                  placeholder="Calle margarita #14"
                  required
                  class="box"
                  v-model="direccion"
                />
              </div>
              <!-- Estado -->
              <div>
                <label for="estado" style="padding-right: 20px;">Estado:</label>
                <select name="" id="estado" class="box" required v-model="estado">
                  <option value="">None</option>
                  <option value="Aguascalientes">Aguascalientes</option>
                  <option value="Ciudad de México">Ciudad de México</option>
                  <option value="Campeche">Campeche</option>
                  <option value="Chiapas">Chiapas</option>
                  <option value="Chihuahua">Chihuahua</option>
                </select>
              </div>
            </b-col>
          </b-row>
        </b-container>
        <div class="btn-position">
          <button type="submit" class="button">Enviar datos</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup>
import axios from 'axios';
import { ref } from 'vue';

// Data
const name = ref('');
const genero = ref('');
const pais = ref('');
const edad = ref();
const direccion = ref('');
const estado = ref('');

// Method POST
const postData = () => {
  axios
    .post('http://localhost:1337/api/interviews', {
      data: {
        name: name.value,
        edad: edad.value,
        genero: genero.value,
        direccion: direccion.value,
        pais: pais.value,
        estado: estado.value,
      },
    })
    .then((res) => {
      console.log(res);
    });

  // Method clean form
  clearForm();
};

// Method clearForm
const clearForm = () => {
  name.value = '';
  genero.value = '';
  pais.value = '';
  edad.value = '';
  direccion.value = '';
  estado.value = '';
};
</script>

<style></style>
