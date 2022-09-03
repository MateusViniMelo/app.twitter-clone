<template>
    <div>
        <header class="p-3 mb-3 border-bottom bg-white">
            <div class="container">
            <div class="d-flex flex-wrap align-items-center justify-content-center justify-content-lg-start">
                <span  class="d-flex align-items-center mb-2 mb-lg-0 text-dark text-decoration-none">
                    
                    <i class="bi bi-twitter me-3 fs-2 text-primary" ></i>
                </span>

                <ul class="nav col-12 col-lg-auto me-lg-auto mb-2 justify-content-center mb-md-0">
                    
                    <li><NuxtLink to="/home" class="nav-link px-2 link-dark">Início</NuxtLink></li>
                    <li><NuxtLink to="/seguir-pessoas" class="nav-link px-2 link-dark">Procurar pessoas</NuxtLink></li>
                    
                </ul>

               

                <div class="dropdown text-end">
                <a href="#" class="d-block link-dark text-decoration-none dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false">
                    <img src="https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460_1280.png" alt="mdo" width="32" height="32" class="rounded-circle">
                    {{$auth.user.name}}
                </a>
                <ul class="dropdown-menu text-small">
                    <li><a class="dropdown-item" href="#">New project...</a></li>
                    <li><a class="dropdown-item" href="#">Settings</a></li>
                    <li><a class="dropdown-item" href="#">Profile</a></li>
                    <li><hr class="dropdown-divider"></li>
                    <li><a class="dropdown-item text-danger logout" @click="logout()" >Sair</a></li>
                </ul>
                </div>
            </div>
            </div>
        </header>
        <div class="container">
            <Nuxt/>
        </div>
    </div>
</template>

<script>
export default {
    head(){
        return {
            link: [
                {
                    href:"https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/css/bootstrap.min.css",
                    rel:"stylesheet",
                    integrity:"sha384-gH2yIJqKdNHPEq0n4Mqa/HGKIhSkIHeL5AyhkYV8i59U5AR6csBvApHHNl/vI1Bx",
                    crossorigin:"anonymous"
                },
                {
                    rel:"stylesheet",
                    href:"https://cdn.jsdelivr.net/npm/bootstrap-icons@1.9.1/font/bootstrap-icons.css"
                },
                {
                    rel:"preconnect",
                    href:"https://fonts.googleapis.com"
                },
                {
                    rel:"preconnect",
                    href:"https://fonts.gstatic.com",
                    crossorigin:"anonymous"
                },
                {
                    href:"https://fonts.googleapis.com/css2?family=Nunito&display=swap",
                    rel:"stylesheet"
                }
            ],
            script: [
                {
                    src:"https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/js/bootstrap.bundle.min.js",
                    integrity:"sha384-A3rJD856KowSb7dwlZdYEkO39Gagi7vIsF0jrRAoQmDKKtQBHUuLZ9AsSv4jD4Xa",
                    crossorigin:"anonymous"
                }
            ]
        }
    },
    methods:{
        async logout(){
            await this.$auth.logout()
        }
    }

}
</script>

<style scoped>
    ul li{
        border-radius: 10px;
    }
    ul li:hover{
        background-color:#e7e7e8;
    }
    .nuxt-link-exact-active{
        font-weight: bold;
    }
    .logout{
        cursor: pointer;
    }
</style>