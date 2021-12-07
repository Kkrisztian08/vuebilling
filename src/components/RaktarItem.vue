<template>
    <tr>
        <td>{{ title }}</td>
        <td>{{ price }}</td>
        <td>{{ quantity }}</td>
        <td><button>Delete</button><button>Edit</button></td>
    </tr>
</template>

<script>
export default {
    props: ['raktar'],
    data() {
        return {
            title: this.raktar.title,
            price: this.raktar.price,
            quantity: this.raktar.quantity
        }
    }
    
}
</script>

<style>
</style>