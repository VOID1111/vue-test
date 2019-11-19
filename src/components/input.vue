<template>
  <div>
    <input @input="update()" type="text" :placeholder="placeholder_val" v-model="data_input">
  </div>
</template>

<script>
export default {
  name: 'input',
  components: {},
  props: ['placeholder', 'text'],
  data() {
    return {
      data_input: ''
    }
  },
  created() {},
  methods: {
    update() {
      this.$emit('input', this.data_input);
    }
  },
  computed: {
    placeholder_val() {
      return this.placeholder ? this.placeholder : ''
    },
    value_val() {
      if (this.text) {
        this.data_input = this.text
      }
    }
  }
}
</script>

<style scoped>
input:active, input:focus {
  outline: none;
}
input {
  width: calc(97% - 2px);
  height: 31px;
  background-color: white;
  border: 1px solid #979595;
  border-radius: 1px;
  font-family: sans-serif;
  font-size: 0.85em;
  font-weight: 500;
  padding-left: 3%;
}
input::placeholder {
  color: #979595;
}
</style>
