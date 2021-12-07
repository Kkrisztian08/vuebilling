<template>
    <table>
        <thead>
            <th>Title</th>
            <th>Price</th>
            <th>Quantity</th>
            <th>Operations</th>
            <th>Összérték</th>
        </thead>
        <tbody>
            <RaktarItem
                v-for="raktar in rows"
                v-bind:key="raktar.title"
                :raktar="raktar"
                @raktar-item-changed="Changed"
                @raktar-item-delete="Delete"
            />
            <tr>
                <td><input type="text" v-model="title" placeholder="Title"></td>
                <td><input type="number" v-model="price" placeholder="Price"></td>
                <td><input type="number" v-model="quantity" placeholder="Quantity"></td>
                <td><button @click="Hozzaad"> Hozzáad</button></td>
                
            </tr>
        </tbody>
    </table>
</template>

<script>
import RaktarItem from './RaktarItem.vue'
export default {
    props: ['rows'],
    components: {RaktarItem},
    methods: {
        Changed(e) {
            this.$emit('raktar-item-changed', e)
        },
        Hozzaad(){
            this.$emit('raktar-item-hozzaad', {
                new:{
                    title:this.title,
                    price:this.price,
                    quantity:this.quantity
                }
            })
            this.title="",
            this.price=null,
            this.quantity=null
        },
        Delete(e){
            this.$emit('raktar-item-delete', e)
        }
    }
}
</script>