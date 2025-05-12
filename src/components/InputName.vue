<template>
  <label for="nome">Nome: </label>
  <input type="text" id="nome" @input="handleChange" v-model="inputValue" required minlength="3"/>
</template>


<script>
export default {
  name: 'InputName',
  emits: ['handleInput'],
  data() {
    return {
      inputValue: ''
    };
  },
  methods: {
    handleChange() {
      this.$emit('handleInput', this.inputValue);
    }
  }
}

</script>