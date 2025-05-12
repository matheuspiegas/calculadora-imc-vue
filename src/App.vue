<template>
  <div class="container">
    <h1>Calculadora de IMC</h1>
    <form class="form-container" @submit="handleSubmit">
      <InputName @handle-input="handleNameChange" />
      <InputHeight @handle-input="handleHeightChange"/>
      <InputWeight @handle-change="handleWeightChange"/>
      <CalculateButton />
    </form>
    <div v-if="formSubmitted">
      <h1>Olá {{ name }}</h1>
      <p>Seu peso é {{ weight }} kg</p>
      <p>Sua altura é {{ height }} cm</p>
      <p>Seu IMC é {{ imc.toFixed(2) }}</p>
    </div>
  </div>
  
</template>

<script>
import InputName from './components/InputName.vue';
import InputHeight from './components/InputHeight.vue';
import InputWeight from './components/InputWeight.vue';
import CalculateButton from './components/CalculateButton.vue';

  export default {
    name: "App",
    data() {
      return {
        name: "",
        height: "",
        weight: "",
        imc: "",
        formSubmitted: false
      }
    },
    components: {
      InputName,
      InputHeight,
      InputWeight,
      CalculateButton
    },
    methods: {
      handleHeightChange(value) {
        this.height = value;
      },
      handleNameChange(value) {
        this.name = value;
      },
      handleWeightChange(value) {
        this.weight = value;
      },
      handleSubmit(event) {
        event.preventDefault();
        this.imc = this.handleCalculate();
        this.formSubmitted = true;
      },
      handleCalculate() {
        const heightInMeters = this.height / 100;
        const imc = this.weight / (heightInMeters * heightInMeters);
        return imc;
      }
    }
  }

</script>


<style>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  html, body {
    height: 100%;
    font-family: Arial, sans-serif;
    background: linear-gradient(to right, #0F2027, #203A43, #2C5364);
  }
  html {
    scroll-behavior: smooth;
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100dvh;
    color: white;
    gap: 1.25rem;
  }

  .form-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  input {
    margin: 0.625rem;
    padding: 0.625rem;
    border-radius: 5px;
    border: 2px solid transparent;
    width: 12.5rem;
  }
  input:focus {
    border-color: #2C5364;
    outline: none;
  }
  label {
    color: #CCC;
    margin-bottom: 0.313rem;
  }
  button {
    background-color: #2C5364;
    color: white;
    border: none;
    padding: 0.625rem 1.25rem;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1rem;
    width: 12.5rem;
  }
  button:hover {
    background-color: #2c53647c;
  }
  
</style>