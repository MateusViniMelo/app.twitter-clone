<template>
   <div class="card mb-4">
        <div class="card-body">
          <span class="fw-bold">{{tweet.usuarios.name}}</span>
          <button type="button" @click="deletarTweet(tweet)"  v-if="$auth.user.id == tweet.id_usuario" class="btn btn-outline-danger btn-sm float-end">Deletar</button>
            <p class="mt-4">
                {{tweet.tweet}}
                
            </p>
          <span class="form-text float-end">{{tweet.created_at}}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: "TweetComponent",
    props: {
        tweet:{
            type: Object
        }
    },
    methods:{
          async deletarTweet(tweet){
             await this.$axios.$delete(`api/tweet/${tweet.id}`)
                .finally(() =>{
                    this.$nuxt.refresh()
                })
            
        }
    }
}
</script>

<style>

</style>