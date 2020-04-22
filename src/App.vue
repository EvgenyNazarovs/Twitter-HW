<template lang="html">
  <div>
    <div id="feed">
      <h3>NewTwitter</h3>
    <div class="addTweetContainer">

    <form v-on:submit.prevent="addNewTweet">
    <h4>Add Tweet</h4>
    <input placeholder="Name" type="text" v-model="newTweet.name">
    <input placeholder="Your @" type="text" v-model="newTweet.handle">
    <label>Choose your avatar</label>
    <select v-model="newTweet.img">
      <option value="https://semantic-ui.com/images/avatar2/large/matthew.png">1</option>
      <option value="https://semantic-ui.com/images/avatar2/large/molly.png">2</option>
      <option value="https://semantic-ui.com/images/avatar2/large/elyse.png">3</option>
    </select>
    <textarea v-model="newTweet.tweet" rows="7" cols="90" placeholder="What's on your mind?"></textarea>
    <input type="submit" value="Post">
    </form>
    </div>

    <h4>Total Likes: {{ totalLikes }}</h4>

    <TweetListItem v-for="(item, index) in tweets" :key="index" :item="item"></TweetListItem>
  </div>
  </div>

</template>

<script>
import TweetListItem from './components/TweetListItem.vue'

export default {
  name: 'App',
  data() {
  return {
    tweets:[
      {
        id: 1,
        name: 'James',
        handle: '@jokerjames',
        img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
        tweet: "If you don't succeed, dust yourself off and try again.",
        likes: 10,
      },
      {
        id: 2,
        name: 'Fatima',
        handle: '@fantasticfatima',
        img: 'https://semantic-ui.com/images/avatar2/large/molly.png',
        tweet: 'Better late than never but never late is better.',
        likes: 12,
      },
      {
        id: 3,
        name: 'Xin',
        handle: '@xeroxin',
        img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
        tweet: 'Beauty in the struggle, ugliness in the success.',
        likes: 18,
        }
      ],
      newTweet: {
        id: 4,
        name: "",
        handle: "",
        img: "",
        tweet: "",
        likes: 1
      },
      filterLikes: 0
    }
  },
  components: {
    TweetListItem
  },
  computed: {
    totalLikes(){
      return this.tweets.reduce((total, tweet) => total + tweet.likes, 0)
    }
  },
  methods: {
    addNewTweet(){
      this.tweets.unshift(this.newTweet);

      this.newTweet = {
        id: 5,
        name: "",
        handle: "",
        img: "",
        tweet: "",
        likes: 1
      }
    },
    }
  }
</script>

<style lang="css" scoped>
body {
  background-color: #e6ecf0;
  margin: 0;
}

#twitter {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.tweet {
  display: flex;
  background-color: red;
  width: 100%;
  max-width: 900px;
  min-height: 110px;
  padding: 10px 20px;
  border-bottom: 1px solid #e6ecf0;
  margin: 0 auto;
}

.addTweetContainer {
  max-width: 65%;
  text-align: center;
  display: flex;
  flex-direction: column;
}

.addTweetContainer textarea {
  font-size: 15px;
  outline: 0px;
  padding: 10px 20px;
}
</style>
