<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <div class="view">
        <div class="container">
          <Form @onSubmit="handleSubmit" />
          <List :tweets="tweets"/>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Form from '@/components/Form.vue';
import List from '@/components/List.vue';

export default {
  components: {
    Form,
    List,
  },
  data() {
    return {
      tweets: [
        {
          id: this.generateId(),
          likes: 0,
          avatar: `https://api.dicebear.com/api/male/1.svg`,
          body: 'hello vue3',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          id: this.generateId(),
          likes: 0,
          avatar: `https://api.dicebear.com/api/male/2.svg`,
          body: 'hello vue3-2',
          date: new Date(Date.now()).toLocaleString(),
        },
      ]
    }
  },
  methods: {
    generateId() {
      const timestamp = Date.now().toString(36); // Convert timestamp to base 36 string
      const randomChars = Math.random().toString(36).substr(2, 5); // Generate random chars
      return `${timestamp}${randomChars}`;
    },
    handleSubmit(tweet) {
      this.tweets.push(tweet);
    }
  }
}
</script>
