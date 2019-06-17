<template>
  <div class="container">

    <h1 class="title is-3 has-text-centered has-text-grey-dark"> Steem Tag Viewer </h1>
    <h2 class="subtitle is-6 has-text-centered has-text-grey-dark">New and Trending STEEMIT posts filtered by Tag</h2>
   
    <div class="field has-addons has-addons-centered">
      <div class="control">
        <input class="input is-rounded" placeholder="Enter Tag Name" type="text" v-model="tag">
      </div>
      <div class="control">
        <a class="button is-idark" v-on:click="pressed()">
          Search
        </a>
      </div>
    </div>

    <h3 v-show="isTrue"> {{answer}} </h3>

  </div>
</template>

<script>
  export default {
    data() {
      return {
        tag: "",
        answer: "",
        isTrue: false
      }
    },
    methods: {
      pressed: function () {
        if (this.tag.indexOf(' ') >= 0) {
          this.isTrue = true
          this.answer = "No Space please"
        } else {
          this.isTrue = false
          this.$emit('updateTag', this.tag)
        }
      },
    }
  }

</script>

<style scoped>

</style>
