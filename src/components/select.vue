<template>
  <div>
    <v-select
      class="select_custom"
      v-model="select"
      :options="items"
      :placeholder="placeholder_val"
      :label="label">
    </v-select>
  </div>
</template>

<script>
import 'vue-select/dist/vue-select.css';

export default {
  name: 'select',
  components: {},
  props: ['placeholder', 'items', 'label'],
  data() {
    return {}
  },
  created() {},
  methods: {},
  computed: {
    placeholder_val() {
      return this.placeholder ? this.placeholder : false
    }
  }
}
</script>

<style>
.select_custom {
  height: 30px;
}
.select_custom .vs__dropdown-toggle {
  background-color: white;
  border: 1px solid #979595;
  border-radius: 1px;
}
.select_custom .vs__search {
  height: 25px;
  color: #979595;
  font-family: sans-serif;
  font-size: 0.85em;
  font-weight: 500;
  padding-left: 3%;
}
.select_custom .vs__selected {
  padding-left: 5px;
  font-family: sans-serif;
  font-size: 0.85em;
  font-weight: 500;
  color: black;
}
.select_custom .vs__dropdown-menu {
  font-family: sans-serif;
  border: 1px solid #979595;
  border-radius: 0 0 1px 1px;;
}
</style>
