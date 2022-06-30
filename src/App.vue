<template>
  <div class="container">
    <div class="row my-5 justify-content-center">
      <div class="col-lg-8">
        <AppTitle title="Invoice Application"></AppTitle>
        <InputForm @add-list="addInvoiceList"></InputForm>
        <ItemTable :lists="lists" @delete="deleteItem" />
        <button class="d-print-none btn btn-primary" @click="printInvoice">Print</button>
      </div>
    </div>
  </div>
</template>

<script>
import AppTitle from './components/AppTitle.vue';
import InputForm from './components/InputForm.vue';
import ItemTable from './components/ItemTable.vue';
export default {
  components: { AppTitle, InputForm, ItemTable },
  data() {
    return {
      lists: [

      ],
    }
  },
  methods: {
    addInvoiceList(quantity, item) {
      item.quantity = quantity;
      item.cost = quantity * item.price;
      // console.log(item)
      this.lists.push(item);
      this.totalCost += item.cost;
    },
    deleteItem(index) {
      console.log(index);
      this.lists.splice(index, 1)
    },
    printInvoice() {
      print();
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Padauk:wght@400;700&family=Roboto:wght@300;400;500;700&display=swap');
@import "bootstrap-icons/font/bootstrap-icons.css";
@import "animate.css/animate.min.css";
@import 'bootstrap/dist/css/bootstrap.min.css';
</style>