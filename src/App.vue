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
import { ref } from 'vue'
import Form from '@/components/Form.vue';
import List from '@/components/List.vue';

export default {
  components: { Form, List },
  setup() {
    const handleSubmit = tweet => tweets.value.push(tweet);
    function generateId() {
      const timestamp = Date.now().toString(36);
      const randomChars = Math.random().toString(36).substr(2, 5);
      return `${timestamp}${randomChars}`;
    };

    const tweets = ref([
      {
        id: generateId(),
        likes: 3,
        avatar: `https://api.dicebear.com/api/male/1.svg`,
        body: 'Ilon Mask',
        date: new Date(Date.now()).toLocaleString(),
      },
      {
        id: generateId(),
        likes: 4,
        avatar: `https://api.dicebear.com/api/male/2.svg`,
        body: 'Jeff Bezos',
        date: new Date(Date.now()).toLocaleString(),
      },
      {
        id: generateId(),
        likes: 2,
        avatar: `https://api.dicebear.com/api/male/3.svg`,
        body: 'Mark Zuckerberg',
        date: new Date(Date.now()).toLocaleString(),
      },
    ]);

    return {
      tweets,
      handleSubmit,
    }
  }
}

// export default {
//   components: {
//     Form,
//     List,
//   },
//   data() {
//     return {
//       tweets: [
//         {
//           id: this.generateId(),
//           likes: 0,
//           avatar: `https://api.dicebear.com/api/male/1.svg`,
//           body: 'hello vue3',
//           date: new Date(Date.now()).toLocaleString(),
//         },
//         {
//           id: this.generateId(),
//           likes: 0,
//           avatar: `https://api.dicebear.com/api/male/2.svg`,
//           body: 'hello vue3-2',
//           date: new Date(Date.now()).toLocaleString(),
//         },
//       ]
//     }
//   },
//   methods: {
//     generateId() {
//       const timestamp = Date.now().toString(36); // Convert timestamp to base 36 string
//       const randomChars = Math.random().toString(36).substr(2, 5); // Generate random chars
//       return `${timestamp}${randomChars}`;
//     },
//     handleSubmit(tweet) {
//       this.tweets.push(tweet);
//     }
//   }
// }
</script>
