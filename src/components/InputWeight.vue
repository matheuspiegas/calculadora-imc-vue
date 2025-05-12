<template>
  <label for="peso">Peso: </label>
  <input type="number" id="peso" v-model="inputValue" @input="handleChange" required/>
</template>


<script>
export default {
  name: 'InputWeight',
  emits: ['handleChange'],
  data() {
    return {
      inputValue: ''
    };
  },
  methods: {
    handleChange() {
      this.$emit('handleChange', this.inputValue);
    }
  }
}

</script>