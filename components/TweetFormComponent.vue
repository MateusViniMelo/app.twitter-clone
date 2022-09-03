<template>

    <div class="card mb-5">
        <div class="card-body">
          <form @submit.prevent="twitar()">
            <div class="form-floating">
              <textarea class="form-control border-light" v-model="formTweet.tweet" placeholder="Pensando..." id="floatingTextarea"></textarea>
              <label for="floatingTextarea" class="fs-5">No que você está pensando?</label>
            </div>
            
            <button type="submit" class="btn btn-primary float-end mt-3" :disabled="formTweet.tweet == '' ">Tweetar</button>
          </form>
        </div>
    </div>

</template>

<script>
export default {
    name: "TweetFormComponent",
    data: () => ({
        formTweet:{
            tweet: "" 
        }
    }),
    methods:{
        async twitar(){
            await this.$axios.$post("/api/tweet", this.formTweet)
                .then(() => {
                    this.$nuxt.refresh()
                })
        }
    }
}
</script>

<style>

</style>