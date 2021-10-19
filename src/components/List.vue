<template>
<select v-model="sortBy">
  <option value="date">Sort by date</option>
  <option value="likes">Sort by likes</option>
</select>
  <ul class="tweets__wrapper">
    <Item 
      v-for="item in sorteredItems" 
      :key="item.id"
      :item="item"
    />
  </ul>
</template>

<script>
import { ref, computed } from '@vue/reactivity'
import Item from './Item.vue'
export default {
  components:{Item},
  props: {
    items: {
      type: Array,
      required: true,
    }
  },

  setup(props) {
    const sortBy = ref('date')

    const sorteredItems = computed(() => {
      return props.items.sort((a, b) => {
        if (a[sortBy.value] > b[sortBy.value]) return -1
        if (a[sortBy.value] < b[sortBy.value]) return 1
      })
    })

    return { sortBy, sorteredItems }
  }
}
</script>