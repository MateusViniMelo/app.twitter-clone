<template>
  <div>
    
        <ul class="list-group">
            
            <li class="list-group-item" v-for="usuario in usuarios" :key="usuario.id">
                {{usuario.name}} 
                <button 
                type="button" 
                :class="usuario.seguindo_sn == 0 ? 'btn btn-primary btn-sm float-end' : 'btn btn-danger btn-sm float-end'" 
                v-text="usuario.seguindo_sn == 0 ? 'Seguir' : 'Deixar de seguir'"
                @click="seguirOuDeixar(usuario)">
                    
                </button>
            </li>
            
           
            
        </ul>
  </div>
</template>

<script>
export default {
    name: "SeguirPessoasComponent",
    props: {
        usuarios:{
            type: Array,
            default: []
        }
    },
    methods:{
        async seguirOuDeixar(usuario){
            const payload = {
                id_usuario: usuario.id
            }
            if(usuario.seguindo_sn == 0){
                await this.$axios.$post("/api/seguir-pessoas",payload)
                    .then(() =>{
                        usuario.seguindo_sn = 1
                    })
            }
            else{
                await this.$axios.$post("/api/deixar-de-seguir",payload)
                    .then(() =>{
                        usuario.seguindo_sn = 0
                    })
            }
        }
    }
}
</script>

<style>

</style>