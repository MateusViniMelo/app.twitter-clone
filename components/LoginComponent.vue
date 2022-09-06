<template>
    <div class="modal-dialog bg-white" id="loginForm" role="document">
        <div class="modal-content rounded-4 shadow">
            
            <div class="modal-header p-5 pb-4 border-bottom-0 ">
                <!-- <h5 class="modal-title">Modal title</h5> -->
                
                <h2 class="fw-bold mb-0 text-center"><img class="mb-4" src="/img/twitter_logo.png" alt="" width="72" height="57"> </img>Entrar no Twitter</h2>
                
                
            </div>

            <div class="modal-body p-5 pt-0">
                <form @submit.prevent="logar()">
                <div class="form-floating mb-3">
                    <input v-model="formLogin.email" type="email" :class="errors.email ? `form-control is-invalid rounded-3` : `form-control rounded-3`" id="floatingInput" placeholder="name@example.com">
                    <label for="floatingInput">Email</label>
                    <div v-if="errors.email" class="invalid-feedback">
                        {{errors.email[0]}}
                    </div>
                </div>
                <div class="form-floating mb-3">
                    <input v-model="formLogin.password" type="password" :class="errors.password ? `form-control is-invalid rounded-3` : `form-control rounded-3`" id="floatingPassword" placeholder="Password">
                    <label for="floatingPassword">Senha</label>
                    <div v-if="errors.password" class="invalid-feedback">
                        {{errors.password[0]}}
                    </div>
                </div>
                <AlertComponent v-if="alert.message" :status="alert.status" :message="alert.message"></AlertComponent>
                <button class="w-100 mb-2 btn btn-lg rounded-3 btn-primary" :disabled="loading" type="submit">
                    <span class="spinner-border spinner-border-sm" v-if="loading" role="status" aria-hidden="true"></span>
                    Entrar

                </button>
                
                <div class="mt-5">
                    <span class="text-muted">Não tem uma conta? </span> <NuxtLink to="/cadastro" class="link-primary">Inscreva-se</NuxtLink>
                </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import AlertComponent from './AlertComponent.vue'
export default {
    name: "LoginComponent",
    data: () => ({
        formLogin: {
            email: "",
            password: ""
        },
        errors: {},
        alert: {
            status: "",
            message: ""
        },
        loading: false
    }),
    methods: {
        async logar() {
            this.loading = true
            await this.$auth.loginWith("local", { data: this.formLogin })
                .catch(error => {
                    if (error.response.status == 422) {
                        this.errors = error.response.data.errors;
                    }
                    else if (error.response.status == 401) {
                        this.errors = {}
                        this.alert = {
                            status: "danger",
                            message: error.response.data.message
                        };
                    }
                    else{
                        this.errors = {}
                        this.alert = {
                            status: "danger",
                            message: "Ops! Não foi possível se conectar com o servidor"
                        };
                    }
                })
                .finally(() => {
                    
                    this.loading = false
                })
        }
    },
    components: { AlertComponent }
}
</script>

<style>
    #loginForm{
        margin-top: 12em;
    }
</style>