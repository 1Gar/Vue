<template>
<div>
  <div class="form">
    <label for='category'>
      <input id='category' type='text' placeholder='Payment description' v-model='category'/>
    </label> <br>
    <label for='value'>
      <input id='value' type='text' placeholder='Payment amount' v-model='value' />
    </label> <br>
    <label for='date'>
      <input id='date' type='text' placeholder='Payment date' v-model='date' />
    </label> <br>
    <Button
    :color='btnForm'
    title="ADD "
    @action='addPayment'
    ></Button>
  </div>
 </div>
</template>

<script>
import Button from './Button.vue'
export default {
  name: 'AddPaymentForm',
  data: () => ({
    value: '',
    category: '',
    date: ''
  }),
  methods: {
    addPayment () {
      const { value, category, date, paymentDay } = this
      const data = {
        value,
        category,
        date: date || paymentDay
      }
      this.$emit('add-payment', data)
    }
  },
  computed: {
    paymentDay () {
      const currentDate = new Date()
      const day = currentDate.getDate()
      const month = currentDate.getMonth() + 1
      const year = currentDate.getFullYear()

      return `${day}.${month}.${year}`
    }
  },
  components: { Button }
}
</script>

<style scoped>
* {
  font-size: 23px;
}
input {
  margin: 5px;
  padding: 5px 12px;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.5);
  border: transparent;
  cursor: pointer;
}
label {
  cursor: pointer;
}
.form{
  text-align: right;
  width: 320px;
}
</style>
