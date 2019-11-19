<template>
  <div>
    <button type="button" :style="background">{{text}}</button>
  </div>
</template>

<script>
export default {
  name: 'button',
  components: {},
  props: ['text', 'color'],
  data() {
    return {}
  },
  created() {},
  methods: {},
  computed: {
    background() {
      return this.color ? `background-color: ` + this.color + `;` : ''
    }
  }
}
</script>

<style scoped>
button {
  padding: 10px 30px;
  font-size: 0.9em;
  font-weight: 400;
  background-color: #727272;
  border: 0;
  color: white;
  transition: all 0.2s;
}
button:hover {
  cursor: pointer;
}
button:active {
  opacity: 0.8;
}
button:active, button:focus {
  outline: none;
}
button::-moz-focus-inner {
  border: 0;
}
</style>
