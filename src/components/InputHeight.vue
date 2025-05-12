<template>
  <label for="altura">Altura: </label>
  <input type="number" id="altura" v-model="inputValue" @input="handleInput" required/>
</template>


<script>
export default {
  name: 'InputHeight',
  emits: ['handleInput'],
  data() {
    return {
      inputValue: ''
    };
  },
  methods: {
    handleInput() {
      this.$emit('handleInput', this.inputValue);
    }
  }
}

</script>