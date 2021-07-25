<template>

  <!-- Browser rendering content -->
  <main class="flex-grow">

    <div class="p-4 grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-3 gap-5">

      <Article
          v-for="post in posts"
          v-bind:key="post.id"
          v-bind:articleId="post.articleId"
          v-bind:title="post.title"
          v-bind:termCondition="post.termCondition"
          v-bind:imgs="post.imgs"
        />

    </div>
  


  </main>
  <!-- Browser rendering content -->
  


</template>

<script>


const axios = require("axios");
const url = process.env.apiURL + '/api_article';

export default {

  async asyncData() {
    let res = 'no'
    try {
      res = (await axios.get(url))
      res = res.data
      console.log(res)
    } catch(e){
      console.error(e)
    }
    return {
      posts: res,
      name: (process.server ? 'server' : 'client')
    }
  }
}



</script>

<style>


</style>