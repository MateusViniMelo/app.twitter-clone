<template>
  <div class="row justify-content-center">
    <div class="col-12 col-md-7 col-lg-6 col-xl-5">
      <login-component></login-component>
    </div>
  </div>
</template>

<script>
import LoginComponent from '../components/LoginComponent.vue'
export default {
  components: { LoginComponent },
  name: 'IndexPage'
}
</script>
