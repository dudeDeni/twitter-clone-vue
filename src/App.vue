<template>
<div class="wrapper">
  <div class="wrapper-content">
    <div class="view">
      <div class="container">
        <Form @onSubmit="handleSubmit"/>
        <List :items="items" />
      </div>
    </div>
  </div>
</div>
</template>

<script>
import { ref } from 'vue'
import List from '@/components/List.vue'
import Form from './components/Form.vue'

export default {
  components: {List, Form},
  setup() {
    const items = ref([
      {
        id: 1,
        body: 'Hello! I did these twitter-clone project to practise Vue 3 with Composition API.',
        likes: 1,
        avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
        date: new Date(Date.now()).toLocaleString(),
      }
    ])

    const handleSubmit = item => {
      items.value.push(item)
    }

    return {
      items,
      handleSubmit
    }
  }
}


/* export default {
  components: {List, Form},
  data() {
    return {
      items: [
        {
          id: 1,
          body: 'Hello! I did these tweeter-clone project to practise Vue 3 with Composition API.',
          likes: 12,
          avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
          date: new Date(Date.now()).toLocaleString(),
        }
      ],
    }
  },

  methods: {
    handleSubmit(item) {
      this.items.push(item)
    }
  }
} */
</script>