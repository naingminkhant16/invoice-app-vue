<template>
    <div>
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th>Id</th>
                    <th>Item</th>
                    <th class="text-end">Price</th>
                    <th class="text-end">Quantity</th>
                    <th class="text-end">Cost</th>
                </tr>
            </thead>
            <tbody>
                <!-- <tr v-for="(list, index) in lists" :key="list.id" class="animate__animated animate__fadeIn"> -->
                <!-- <td>{{ index + 1 }}</td>
                    <td class="d-flex justify-content-between">
                        {{ list.name }} <i @click="deleteItem(index)" class="bi bi-trash text-danger"></i>
                    </td>
                    <td class="text-end">{{ list.price }}</td>
                    <td class="text-end">{{ list.quantity }}</td>
                    <td class="text-end">{{ list.cost }}</td> -->
                <!-- </tr> -->
                <TableRow v-for="(list, index) in lists" :key="list.id" :list="list" :currentIndex="index"
                    @deleteItem="deleteItem">
                </TableRow>
            </tbody>
            <tfoot>
                <tr>
                    <td colspan="4" class="text-center">Total</td>
                    <td>{{ total }}</td>
                </tr>
            </tfoot>
        </table>
    </div>
</template>

<script>
import TableRow from './TableRow.vue';
export default {
    props: {
        lists: Object,
    },
    computed: {
        total() {
            return this.lists.reduce((p, c) => p + c.cost, 0);
        }
    },
    methods: {
        deleteItem(index) {
            this.$emit("delete", index);
        }
    },
    components: { TableRow }
}
</script>

<style lang="scss" scoped>
</style>