<template>
    <div class="border rounded p-3 my-4 d-print-none">
        <form action="" @submit.prevent="addItem">
            <div class="row g-3">
                <div class="col-md-6">
                    <div class="">
                        <label for="">Select Item</label>
                        <select required v-model="selectedItem" class="form-select">
                            <option v-for="item in items" :key="item.id" :value="item.id">{{ item.name }}</option>
                        </select>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="">
                        <label for="">Quantity</label>
                        <input required class="form-control" v-model="quantity" type="number">
                    </div>
                </div>
                <div class="col-md-3">
                    <button class="btn btn-primary btn-sm w-100 h-100">
                        <div v-if="isLoading" class="spinner-grow spinner-grow-sm text-light" role="status">
                            <span class="visually-hidden">Loading...</span>
                        </div>
                        <i v-else class="bi bi-plus-circle-dotted me-2"></i>
                        Add Item
                    </button>
                </div>
            </div>
        </form>
    </div>
</template>

<script>
// import { setTimeout } from 'timers/promises';

export default {
    data() {
        return {
            items: [
                {
                    id: 1,
                    name: "Appple",
                    price: 400
                },
                {
                    id: 2,
                    name: "Orange",
                    price: 450
                },
                {
                    id: 3,
                    name: "Banana",
                    price: 500
                }, {
                    id: 4,
                    name: "Pineapple",
                    price: 700
                },
            ],
            quantity: Math.ceil(Math.random() * 10),
            selectedItem: null,
            isLoading: false
        }
    },
    methods: {
        addItem() {
            this.isLoading = true;
            setTimeout(() => {
                this.$emit('addList', this.quantity, this.items.find(item => item.id == this.selectedItem));
                this.selectedItem = null;
                this.quantity = Math.ceil(Math.random() * 10);
                this.isLoading = false;
            }, 500);
        }
    }
}
</script>

<style lang="scss" scoped>
</style>