<template>
  <form @submit.prevent="onSubmit">
      <textarea
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
export default {
  data() {
    return {
      body: ''
    }
  },
  methods: {
    generateId() {
      const timestamp = Date.now().toString(36); // Convert timestamp to base 36 string
      const randomChars = Math.random().toString(36).substr(2, 5); // Generate random chars
      return `${timestamp}${randomChars}`;
    },
    onSubmit() {
      const newTweet = {
        id: this.generateId(),
        likes: 0,
        avatar: `https://api.dicebear.com/api/male/${Date.now()}.svg`,
        body: this.body,
        date: new Date(Date.now()).toLocaleString(),
      }
      this.$emit('onSubmit', newTweet);
      this.body = "";
    }
  }
}
</script>
