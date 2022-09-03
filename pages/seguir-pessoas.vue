<template>
  <div class="row justify-content-center">
    <div class="col-12 col-md-8 col-lg-6 col-xl-5">
        <h3 class="card-title mb-3 mt-5">Encontrar amigos</h3>
       
       <SeguirPessoasComponent :usuarios="usuarios"></SeguirPessoasComponent>
    </div>
  </div>
</template>

<script>
import SeguirPessoasComponent from '~/components/SeguirPessoasComponent.vue';
export default {
    name: "SeguirPessoasPage",
    layout: "auth",
    async asyncData({ $axios }) {
        const usuarios = await $axios.$get("api/seguir-pessoas");
        return { usuarios };
    },
    components: { SeguirPessoasComponent }
}
</script>

<style>

</style>