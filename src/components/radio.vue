<template>
  <div>
    <label class="container">{{label}}
      <input @input="update()" type="radio" id="radio1" :value="value" v-model="radio_val">
      <span class="checkmark"></span>
    </label>
  </div>
</template>

<script>
import 'vue-select/dist/vue-select.css';

export default {
  name: 'select',
  components: {},
  props: ['value', 'label', 'radio_modal'],
  data() {
    return {
      radio_val: ''
    }
  },
  created() {},
  methods: {
    update() {
      this.$emit('input', this.radio_val);
    }
  },
  computed: {
    value_val() {
      if (this.radio_modal) {
        this.radio_val = this.radio_modal
      }
    }
  }
}
</script>

<style>
</style>
