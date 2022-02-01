<template>
  <div class="home">
    <Tweet 
      v-for="tweet in tweets" 
      :key="tweet._id" 
      :tweet="tweet" />
  </div>
</template>

<script>
import { ref } from 'vue';
import Tweet from '../components/Tweet';
import vweets from '../vweets';

export default {
  setup () {
    const tweets = ref(vweets);

    return {
      tweets,
      Tweet
    }
  }
}
</script>
