<template>
<div>
  <div class="form">
    <label for='category'>
      <select id="category" v-model="category">
        <option
            v-for="category of categoryList"
            :value="category"
            :key="category"
        >
          {{ category }}
        </option>
      </select>
    </label>
    <label for='value'>
      <input id='value' type='text' placeholder='Payment amount' v-model='value' />
    </label>
    <label for='date'>
      <input id='date' type='text' placeholder='Payment date' v-model='date' />
    </label>
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
  props: {
    categoryList: {
      type: Array,
      default: () => []
    }
  },
  data: () => ({
    value: '',
    category: '',
    date: ''
  }),
  methods: {
    resetData () {
      this.value = ''
      this.category = ''
      this.date = ''
    },
    addPayment () {
      const { value, category, date, paymentDay } = this
      const data = {
        value: +value,
        category,
        date: date || paymentDay
      }
      this.$emit('add-payment', data)
      this.resetData()
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
select{
  box-sizing: border-box;
  height: 38px;
  width: 305px;
  margin: 5px;
  border: transparent;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.5);

}
</style>
