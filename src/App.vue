<template>
  <div id="app">

    <header>
      <div class="header">My personal costs</div>
    </header>

    <main>
      <AddPaymentForm @add-payment="addPayment" v-if="isOpen"></AddPaymentForm>
      <div class="downBtn">
      <Button :title="isOpen ? 'CLOSE NEW COSTS ' : 'ADD NEW COSTS '" @action='clickBtn'></Button>
      </div>
      <PaymentDisplay :items="paymentsList"/>
    </main>
  </div>
</template>

<script>
import PaymentDisplay from '@/components/PaymentDisplay.vue'
import AddPaymentForm from '@/components/AddPaymentForm.vue'
import Button from '@/components/Button.vue'

export default {
  name: 'App',
  components: {
    AddPaymentForm,
    PaymentDisplay,
    Button
  },
  data: () => ({
    show: true,
    counter: 0,
    paymentsList: [],
    isOpen: false
  }),
  methods: {
    addPayment (data) {
      this.paymentsList.push(data)
    },
    clickBtn () {
      this.isOpen = !this.isOpen
    }
  },
  created () {}
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0 auto;
  margin-top: 60px;
  font-size: 23px;
  width: 1240px
}
.header{
font-size: 40px;
margin-bottom: 0px;
font-weight: 400px;
text-align: left;
}
.downBtn {
  display: flex;
}
</style>
