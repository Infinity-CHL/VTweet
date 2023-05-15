<template>
  <form @submit.prevent="onSubmit">
      <textarea
        class="textarea"
        v-model="body"
        required
        placeholder="Type tweet here"
      />
      <br>
      <button
        type="submit"
        class="btn btnTweet"
      >
        Tweet
      </button>
    </form>
</template>

<script>
import { ref } from 'vue';

export default {
  setup(_, { emit }) {
    const body = ref('');
    function generateId() {
      const timestamp = Date.now().toString(36);
      const randomChars = Math.random().toString(36).substr(2, 5);
      return `${timestamp}${randomChars}`;
    };

    const onSubmit = () => {
      const newTweet = {
        id: generateId(),
        likes: 0,
        avatar: `https://api.dicebear.com/api/male/${Date.now()}.svg`,
        body: body.value,
        date: new Date(Date.now()).toLocaleString(),
      }
      emit('onSubmit', newTweet);
      body.value = "";
    }
    return {
      body,
      onSubmit,
    }
  }
}
</script>
