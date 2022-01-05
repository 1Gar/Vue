---<template>
  <div>
    <div class="main">
      <label for="op1">
        <input id="op1" type="text" v-model="op1" value="" />
      </label>

      <label for="op2">
        <input id="op2" type="text" v-model="op2" value="" />
      </label>
      = {{ result }}
    </div>
    <div class="keyboard">
      <button @click="calculate(op)" v-for="op in operations" :key='op'>{{op}}</button>
    </div>
    <label for="keyBoard">Отобразить экранную клавиатуру <input type="checkbox" id="keyBoard" @click="toggleElement"></label>
    <div class="element" v-if="isElVisible">
      <button @click="input(n)" v-for="n in calculatorElements" :key='n'>{{n}}</button>
      <button @click="remove()">delete</button>
      <button @click="clear()">clear</button>
      <br>
      <label><input type="radio" id="one" value="Операнд 1" name="" v-model="radioButtons">Операнд 1</label>
      <label><input type="radio" id="one" value="Операнд 2" name="" v-model="radioButtons">Операнд 2</label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalculatorComp',
  data: () => ({
    op1: '',
    op2: '',
    result: 0,
    isElVisible: false,
    calculatorElements: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
    operations: ['+', '-', '/', '*', '//', '**'],
    radioButtons: 'Операнд 1'
  }),
  methods: {
    input: function (char) {
      if (this.radioButtons === 'Операнд 1') {
        this.op1 += char
      } else {
        this.op2 += char
      }
    },
    remove: function () {
      if (this.radioButtons === 'Операнд 1') {
        this.op1 = this.op1.slice(0, -1)
      } else {
        this.op2 = this.op2.slice(0, -1)
      }
    },
    clear: function () {
      this.result = '0'
      this.op1 = ''
      this.op2 = ''
    },
    toggleElement () {
      this.isElVisible = !this.isElVisible
    },
    sum () {
      this.result = +this.op1 + +this.op2
    },
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
    },
    calculate (operation) {
      switch (operation) {
        case '+': this.sum(); break
        case '-': this.sub(); break
        case '/': this.div(); break
        case '//': this.divInt(); break
        case '**': this.degr(); break
        case '*': this.mult(); break
      }
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
  cursor:pointer;
}
input{
  margin: 5px;
  padding: 5px 12px;
  box-shadow: 0 0 3px rgba(0,0,0,0.5);
}
#keyBoard{
  transform:scale(1.3);
  opacity:0.9;
  cursor:pointer;
}
label{
  cursor:pointer;
}
#one{
  transform:scale(1.3);
  opacity:0.9;
  cursor:pointer;
  margin: 20px;
}
</style>
