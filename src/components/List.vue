<template>
  <select v-model="sortBy" class="select">
    <option
      v-for="option in options"
      :key="option.value"
      :value="option.value"
    >
      Sort by{{ option.text }}
    </option>
  </select>
  <div class="tweets__content">
    <ul class="tweets__wrapper">
      <Item
        v-for="tweet in sorteredTweets"
        :key="tweet.id"
        :tweet="tweet"
      />
    </ul>
  </div>
</template>

<script>
import { ref, computed } from 'vue';
import Item from '@/components/Item.vue';

export default {
  components: {
    Item,
  },
  props: {
    tweets: {
      type: Array,
      required: true,
    }
  },
  setup({ tweets }) {
    const sortBy = ref('date');
    const options = ref([
      { value: 'date', text: 'date' },
      { value: 'likes', text: 'likes' },
    ]);

    const sorteredTweets = computed(() => {
      return tweets.sort((a, b) => {
        if (a[sortBy.value] > b[sortBy.value]) return -1;
        if (a[sortBy.value] < b[sortBy.value]) return 1;
      });
    });

    return {
      sortBy,
      options,
      sorteredTweets,
    }
  }
}
</script>
