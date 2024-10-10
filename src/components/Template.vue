<template>
    <div class="main-container">
      <form class="form-container">
        <fieldset>
          <div>
            <label for="color-cuadrado">Color de fondo:</label>
            <input
              type="text"
              v-model="colorCuadrado"
              id="color-cuadrado"
              class="input-width"
            />
          </div>
  
          <div>
            <label for="color-letra">Color de texto:</label>
            <input
              type="text"
              v-model="colorLetra"
              id="color-letra"
              class="input-width"
            />
          </div>
        </fieldset>
  
        <fieldset>
          <div class="checkbox-container">
            <label>Mostrar texto</label>
            <input type="checkbox" v-model="show" />
          </div>
  
          <div>
            <label for="border">Borde:</label>
            <input
              type="range"
              v-model="border"
              id="border"
              min="1"
              max="50"
            />
          </div>
  
          <div>
            <label for="texto">Contenido textual:</label>
            <textarea
              v-model="texto"
              id="texto"
              class="input-width textarea-spacing"
              :style="{ maxHeight: '100px' }"
            ></textarea>
          </div>
  
          <div>
            <label for="tipografia">Tipografía:</label>
            <select v-model="typography" id="tipografia" class="input-width">
              <option v-for="tipo in tipografias" :key="tipo" :value="tipo">
                {{ tipo }}
              </option>
            </select>
          </div>
  
          <div class="checkbox-container">
            <label>Opaco</label>
            <input type="checkbox" v-model="opaco" />
          </div>
  
          <div>
            <label>Tamaño de letra:</label>
            <div class="radio-container">
              <label>
                <input type="radio" v-model="size" value="1rem" />
                Pequeño
              </label>
              <label>
                <input type="radio" v-model="size" value="1.5rem" />
                Mediano
              </label>
              <label>
                <input type="radio" v-model="size" value="2rem" />
                Grande
              </label>
            </div>
          </div>
        </fieldset>
      </form>
  
      <div
        id="square"
        :style="{
          backgroundColor: colorCuadrado || '#80b280',
          color: colorLetra || 'white',
          borderRadius: radioCompleto,
          fontSize: size,
          opacity: opaco ? 0.5 : 1,
          fontFamily: typography,
          fontWeight: 'bold'
        }"
        :class="[typography, { opaque: opaco }]"
        v-show="show"
      >
        {{ texto }}
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "Template",
    data() {
      return {
        colorCuadrado: "",
        colorLetra: "",
        show: true,
        border: "",
        texto: "Awesome Vue.js",
        typography: "font-sans-serif",
        opaco: false,
        size: "1rem",
        tipografias: [
          "font-sans-serif",
          "font-monospace",
          "font-serif",
          "font-weight-bold",
          "font-italic",
          "text-uppercase",
        ],
      };
    },
    computed: {
      radioCompleto() {
        return this.border + "%";
      },
    },
  };
  </script>
  
  <style scoped>
  html, body {
    height: 100%;
    margin: 0;
  }
  
  .main-container {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
  
  .form-container {
    background: darkslategray;
    color: white;
    padding: 1rem;
    font-size: 16px;
    border-radius: 8px;
    margin-right: 2rem;
  }
  
  fieldset {
    border: none;
    margin: 0 0 1rem;
  }
  
  label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: bold; 
  }
  
  .checkbox-container {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-bottom: 0.5rem;
  }
  
  .checkbox-container label {
    margin-right: 0.5rem;
  }
  
  fieldset,
  input,
  select,
  textarea {
    margin-bottom: 0.5rem;
  }
  
  .input-width,
  textarea,
  select {
    width: 250px;
    display: block;
  }
  
  .textarea-spacing {
    margin-top: 1rem;
  }
  
  .radio-container {
    display: flex;
    gap: 1rem;
  }
  
  #square {
    width: 400px;
    height: 400px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
    border-radius: 0;
    overflow: hidden;
    background-color: #80b280;
    color: white;
    text-align: center;
  }
  
  .opaque {
    opacity: 0.5;
  }
  </style>