<template>
    <tr class="animate__animated animate__flip">
        <td>{{ currentIndex + 1 }}</td>
        <td class="">
            <div class="d-flex justify-content-between">
                <span>{{ list.name }} </span>
                <div v-if="isDeleting" class="spinner-border spinner-border-sm text-danger" role="status">
                    <span class="visually-hidden">Loading...</span>
                </div>
                <i v-else @click="deleteItem(currentIndex)" class="bi bi-trash text-danger"></i>
            </div>
        </td>
        <td class="text-end">{{ list.price }}</td>
        <td class="text-end">{{ list.quantity }}</td>
        <td class="text-end">{{ list.cost }}</td>
    </tr>
</template>

<script>
import Swal from 'sweetalert2'
export default {
    props: {
        list: Object,
        currentIndex: Number
    }, data() {
        return {
            isDeleting: false
        }
    }, methods: {
        deleteItem(index) {
            Swal.fire({
                title: 'Are you sure?',
                text: "You won't be able to revert this!",
                icon: 'warning',
                showCancelButton: true,
                confirmButtonColor: '#3085d6',
                cancelButtonColor: '#d33',
                confirmButtonText: 'Yes, delete it!'
            }).then((result) => {
                if (result.isConfirmed) {
                    this.isDeleting = true;
                    setTimeout(() => {
                        this.$emit('deleteItem', index);
                        Swal.fire(
                            'Deleted!',
                            'Your list has been deleted.',
                            'success'
                        )
                    }, 1000)
                }
            })
        }
    },
}
</script>

<style lang="scss" scoped>
</style>