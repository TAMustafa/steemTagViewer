<template>
  <div id="app">

    <div class="container">
      <Jumbo v-on:updateTag="runTag($event)" />

      <div class="container" v-if="isTrue">
        <div class="columns">

          <!-- Mark: Trending Section -->
          <div class="column">
            <i class="fas fa-poll" aria-hidden="true"></i>
            <strong>Trending</strong>
            <Trending v-bind:trending="trending" />
          </div>

          <!-- Mark: New Section -->
          <div class="column">
            <i class="fas fa-rss" aria-hidden="true"></i>
            <strong>New</strong>
            <New v-bind:news="news" />
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import steem from "steem"
  import New from "./components/New.vue"
  import Trending from "./components/Trending.vue"
  import Jumbo from "./components/Jumbo.vue"

  export default {
    name: "app",
    data() {
      return {
        tag: "",
        trending: [],
        news: [],
        isTrue: false
      }
    },

    components: {
      Jumbo,
      New,
      Trending
    },

    methods: {

      runTag(updatedTag) {
        this.tag = updatedTag
        this.runTrending(),
          this.runNew(),
          this.isTrue = true
      },

      runNew: function () {
        var query = {
          "tag": this.tag,
          "limit": 20
        }
        steem.api.getDiscussionsByCreated(query, (err, result) => this.news = result)
      },

      runTrending: function () {
        var query = {
          "tag": this.tag,
          "limit": 20
        }
        steem.api.getDiscussionsByTrending(query, (err, result) => this.trending = result)
      }
    }
  }

</script>

<style>
@import "~bulma/css/bulma.css";
</style>
