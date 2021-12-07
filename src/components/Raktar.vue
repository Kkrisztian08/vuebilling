<template>
  <div>
      <table>
          <thead>
            <tr>
                <th>Title</th>
                <th>Price</th>
                <th>Quantity</th>
                <th>Operations</th>
            </tr>
        </thead>
        <tbody>
            <RaktarItem
                v-for="raktar in rows"
                v-bind:key="raktar.title"
                :raktar="raktar"
                @raktar-item-changed="Changed"
                @raktar-item-delete="Delete"
            />
            <td><input type="text"></td>
            <td><input type="number"></td>
            <td><input type="number"></td>
            <td><button  @click="Hozzaad">Hozzáad</button></td>
        </tbody>
          
      </table>
  </div>
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