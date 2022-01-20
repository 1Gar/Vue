<template>
<div>
<table class="table table-bold"><tr><td>#</td><td>Date</td><td>Category</td><td>Value</td></tr></table>
  <div v-for="(item, index) in items" :key="index"><table class="table">
    <tr><td>{{index+1}}</td><td>{{item.date}}</td><td>{{item.category}}</td><td>{{item.value}}</td></tr>
    </table></div>
</div>
</template>

<script>
export default {
  name: 'PaymentDisplay',
  props: {
    items: {
      type: Array,
      default: () => ([])
    },
    show: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped>
.table {
border-bottom: 1px solid rgb(214, 208, 208);
margin-left: 0px;
}
.table-bold{
  font-size: 20px;
  font-weight: bold;
}
td{
width: 134px;
height: 50px;
}
</style>
