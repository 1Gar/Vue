---<template>
  <div>
    <div class="main">
      <label for="op1">
        <input id="op1" type="number" v-model.number="op1" />
      </label>

      <label for="op2">
        <input id="op2" type="number" v-model.number="op2" />
      </label>
      = {{ result }}
    </div>
    <div class="keyboard">
      <button @click="result = op1 + op2">Сложение</button>
      <button @click="sub">Вычитание</button>
      <button @click="div">Деление</button>
      <button @click="divInt">Целочисленное деление</button>
      <button @click="mult">Умножение</button>
      <button @click="degr">Возведение в степень</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalculatorComp',
  data: () => ({
    op1: 0,
    op2: 0,
    result: 0
  }),
  methods: {
    sub () {
      this.result = this.op1 - this.op2
    },

    div () {
      this.result = this.op1 / this.op2
    },

    divInt () {
      this.result = parseInt(this.op1 / this.op2)
    },

    degr () {
      this.result = this.op1 ** this.op2
    },

    mult () {
      this.result = this.op1 * this.op2
    }
  }
}
</script>

<style scoped>
*{
  font-size: 23px;
}
button{
  margin: 20px 5px;
  padding: 5px 12px;
  box-shadow: 0 0 3px rgba(0,0,0,0.5);
}
input{
  margin: 5px;
  padding: 5px 12px;
  box-shadow: 0 0 3px rgba(0,0,0,0.5);
}
</style>
