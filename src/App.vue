<template>
  <div id="app">

    <header>
      <div class="header">My personal costs</div>
    </header>

    <main>
      <div class="header">Total: {{ paymentsListTotalAmount }}</div>
      <AddPaymentForm @add-payment="addPayment" v-if="isOpen" :categoryList="categoryList"></AddPaymentForm>
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
import { mapMutations, mapActions, mapGetters } from 'vuex'

export default {
  name: 'App',
  components: {
    AddPaymentForm,
    PaymentDisplay,
    Button
  },
  data: () => ({
    // show: true,
    // counter: 0,
    // paymentsList: [],
    isOpen: false
  }),
  methods: {
    ...mapMutations(['ADD_PAYMENT_DATA']),
    ...mapActions(['fetchData', 'fetchCategoryList']),
    addPayment (data) {
      // this.paymentsList.push(data)
      this.ADD_PAYMENT_DATA(data)
    },
    clickBtn () {
      this.isOpen = !this.isOpen
    }
  },
  computed: {
    ...mapGetters([
      'paymentsList',
      'paymentsListTotalAmount',
      'categoryList'
    ])
  },
  created () {
    console.log(this.$store)
    this.fetchData()
    this.fetchCategoryList()
  }
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
