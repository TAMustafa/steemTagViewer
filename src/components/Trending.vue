<template>

  <div class="box">
    <div class="box" v-for="trend in trending" :value="trend" :key="trend">
    <article class=" media">

      <div class="media-left">
        <figure class="image is-64x64">
          <img class="is-rounded" :src="'https://steemitimages.com/u/' + trend.author + '/avatar'">
        </figure>
      </div>

      <div class="media-content">
        <div class="content">
          <p>
            <strong class="has-text-grey-dark">{{trend.author}}</strong>
            <br>
            <a :href="'http://steemit.com' + trend.url" target="_blank"> {{ trend.root_title }} </a>
          </p>
        </div>

        <nav class="level">
          <div class="level-left">
            <span class="icon is-small level-item">
              <i class="far fa-thumbs-up"></i>
            </span>

            <span>
              {{ trend.active_votes.length }}
            </span>
          </div>

          <div class="level-right">
            <span class="icon is-small level-item">
              <i class="far fa-clock"></i>
            </span>

            <span>
              {{ trend.created }}
            </span>
          </div>
        </nav>

      </div>
      </article>
    </div>
  </div>

</template>

<script>
  export default {
    props: ["trending"]
  }
</script>