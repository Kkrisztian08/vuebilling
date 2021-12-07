<template>
  <tr>
    <td v-if="edit"><input type="text" v-model="title" v-bind="title"></td>
    <td v-if="edit"><input type="number" v-model="price" v-bind="price"></td>
    <td v-if="edit"><input type="number" v-model="quantity" v-bind="quantity"></td>
    <td v-if="edit"><button @click="Save">Save</button></td>
    
    <td v-if="!edit">{{title}}</td>
    <td v-if="!edit">{{price}}</td>
    <td v-if="!edit">{{quantity}}</td>
    <td v-if="!edit"><button @click="Delete">X</button> <button @click="Edit">Edit</button></td>
    <td v-if="!edit">{{quantity*price}}</td>
  </tr>
</template>

<script>
export default {
    props: ['raktar'],
    data() {
        return {
            title: this.raktar.title,
            price:this.raktar.price,
            quantity:this.raktar.quantity,
            edit:false
        }
    },
    methods: {
        Edit() {
            this.edit = true
        },
        Save() {
            this.edit = false
            this.$emit('raktar-item-changed', {
                original: this.raktar,
                new: {
                    title: this.title,
                    price:this.price,
                    quantity:this.quantity
                    },
            })
        },
        Delete(){
            this.$emit('raktar-item-delete',{
                original:this.raktar
            })
        }
    }
}
</script>

<style>
</style>