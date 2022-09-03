<template>
  <div class="row justify-content-center">
    <div class="col-12 col-md-6 col-lg-4 col-xl-3 border-end border-bottom mb-4">
      <ProfileComponent :quantidadeTweets="data.quantidadeTweets" :quantidadeSeguidores="data.quantidadeSeguidores" :quantidadeUsuariosSeguindo="data.quantidadeUsuariosSeguindo"></ProfileComponent>
    </div>
    <div class="col-12 col-md-6 col-xl-6 ">
      <TweetFormComponent></TweetFormComponent>
      <TweetComponent v-for="tweet in data.tweets" :key="tweet.id" :tweet="tweet"></TweetComponent>
    </div>
    <div class="col"><pre></pre></div>
  </div>
</template>

<script>
import ProfileComponent from '~/components/ProfileComponent.vue';
import TweetComponent from '~/components/TweetComponent.vue';
import TweetFormComponent from '~/components/TweetFormComponent.vue';
export default {
    middleware: "auth",
    layout: "auth",
    components: { ProfileComponent, TweetComponent, TweetFormComponent },

    async asyncData({$axios}){
      const data = await $axios.$get("api/tweet")

      return {data}
    }
}
</script>

<style>

</style>