<template>
  <ul class="tweets__wrapper">
    <Item
      v-for="tweet in tweets"
      :key="tweet.id"
      :tweet="tweet"
    />
  </ul>
</template>

<script>
import Item from '@/components/Item.vue';
export default {
  components: {
    Item
  },
  props: {
    tweets: {
      type: Array,
      required: true,
    }
  }
}
</script>
