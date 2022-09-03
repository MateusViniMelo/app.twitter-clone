<template>
    <div class="modal-dialog bg-white" id="loginForm" role="document">
        <div class="modal-content rounded-4 shadow">
            <div class="modal-header p-5 pb-4 border-bottom-0">
                <!-- <h5 class="modal-title">Modal title</h5> -->
                
                <h2 class="fw-bold mb-0">Criar uma conta</h2>
                <span>
                    <NuxtLink to="/">Voltar</NuxtLink>
                </span>
                
                
            </div>

            <div class="modal-body p-5 pt-0">
                <form @submit.prevent="cadastrar()">
                    <div class="form-floating mb-3">
                        <input v-model="formRegister.name" type="text" :class="errors.name ? `form-control is-invalid rounded-3` : `form-control rounded-3`" id="floatingInputName" placeholder="Nome">
                        <label for="floatingInputName">Nome</label>
                        <div v-if="errors.name" class="invalid-feedback">
                            {{errors.name[0]}}
                        </div>
                    </div>
                    <div class="form-floating mb-3">
                        <input v-model="formRegister.email" type="email" :class="errors.email ? `form-control is-invalid rounded-3` : `form-control rounded-3`" id="floatingInput" placeholder="Email">
                        <label for="floatingInput">Email</label>
                        <div v-if="errors.email" class="invalid-feedback">
                            {{errors.email[0]}}
                        </div>
                    </div>
                    <div class="form-floating mb-3">
                        <input v-model="formRegister.password" type="password" :class="errors.password ? `form-control is-invalid rounded-3` : `form-control rounded-3`" id="floatingPassword" placeholder="Password">
                        <label for="floatingPassword">Senha</label>
                        <div v-if="errors.password" class="invalid-feedback">
                            {{errors.password[0]}}
                        </div>
                    </div>
                    <AlertComponent v-if="alert.message" :status="alert.status" :message="alert.message"></AlertComponent>
                    <button class="w-100 mb-2 btn btn-lg rounded-3 btn-primary" :disabled="loading" type="submit">
                        <span class="spinner-border spinner-border-sm" v-if="loading" role="status" aria-hidden="true"></span>
                        Cadastrar

                    </button>
                
               
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "UsuarioCadastroComponent",
    data: () => ({
         formRegister: {
            name: "",
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
    methods:{
        async cadastrar(){
            await this.$axios.$post("/api/auth/register", this.formRegister)
                .then(() => {
                    this.alert = {
                        status: "success",
                        message: "Usuário cadastrado com sucesso"
                    }
                    this.errors = {}
                    this.formRegister = {}
                })
                .catch(error => {
                    if(error.status = 422){
                        this.errors = error.response.data.errors
                    }
                })
        }
    }
}
</script>

<style>

</style>