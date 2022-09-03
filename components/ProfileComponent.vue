<template>
    <div>
        <div class="card">
            <div class=" profile-cover"></div>
            <div class="card-body">
                <p class="fw-bold fs-5">{{$auth.user.name}}</p>
                <div class="row justify-content-center">
                    <div class="col-4">
                        <div class="fw-bold form-text text-center">
                            Tweets<br>
                            <span class="text-center text-primary">{{quantidadeTweets}}</span>
                        </div>
                        
                    </div>
                    <div class="col-4">
                        <div class="fw-bold form-text text-center">
                            Seguidores<br>
                            <span class="text-center text-primary">{{quantidadeSeguidores}}</span>
                        </div>
                    </div>
                    <div class="col-4">
                        <div class="fw-bold form-text text-center">
                            Seguindo<br>
                            <span class="text-center text-primary">{{quantidadeUsuariosSeguindo}}</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "ProfileComponent",
    props:{
        quantidadeTweets:{
            type: Number,
        },
        quantidadeSeguidores:{
            type: Number,
             
        },
        quantidadeUsuariosSeguindo:{
            type: Number
        }
    }
}
</script>

<style scoped>
    .profile-cover{
        height: 80px;
        background-color: #28a0d5 ;
    }
</style>