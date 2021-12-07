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
            />
        </tbody>
          
      </table>
  </div>
</template>

<script>
import RaktarItem from './RaktarItem.vue'
export default {
    props: ['rows'],
    components: {RaktarItem}
}
</script>