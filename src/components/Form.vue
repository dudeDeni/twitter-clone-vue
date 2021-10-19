<template>
  <form @submit.prevent="onSubmit">
    <textarea
      v-model="body"
      required placeholder="Type tweet here"
    >
    </textarea>
    <button class="btn btnTweet" type="submit">Post tweet</button>
  </form>
</template>

<script>
import { ref } from 'vue'
export default {
emits: ['onSubmit'],

  setup(_, context) {
    const body = ref('')
    
    const onSubmit = () => {
      context.emit('onSubmit', {
        id: Math.round(Math.random() * 10),
        body: body.value,
        likes: 0,
        avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
        date: new Date(Date.now()).toLocaleString(),
      })
      body.value = ''
    }
    return { body, onSubmit }

  }
}
/* export default {
  data() {
    return {
      body: '',
    }
  },
  methods: {
    onSubmit() {
      this.$emit('onSubmit', {
        id: Math.round(Math.random() * 10),
        body: this.body,
        likes: 0,
        avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
        date: new Date(Date.now()).toLocaleString(),
      })
      this.body = '';
    }
  }
} */
</script>