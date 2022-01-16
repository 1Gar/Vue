<template>
  <div>
    <button @click="$emit('action')">{{ title }} <i class="fas fa-plus"></i></button>
  </div>
</template>

<script>
export default {
  name: 'Button',
  emits: ['action'],
  props: {
    title: {
      type: String,
      default: '',
      validator (value) {
        return ['', 'ADD', 'ADD NEW COSTS'].includes(value)
      }
    }
    // color: {
    //   type: String,
    //   default: '',
    //   validator (value) {
    //     return ['', 'btn-form', 'primary'].includes(value)
    //   }
    // }
  },
  data: () => ({}),
  methods: {},
  computed: {}
}
</script>

<style scoped>
* {
  font-size: 20px;
}

.btn-form {
  width: 160px;
  margin: 5px 0 5px 0;
}
.primary {
  font-size: 19px;
  width: 260px;
}
button {
  box-sizing: border-box;
  margin: 20px 5px;
  padding: 5px 12px;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.5);
  cursor: pointer;
  background-color: rgb(0, 168, 155);
  color: white;
  border: transparent;
  margin: 8px 0 0 0;
}
</style>
