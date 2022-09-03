<template>
  <div class="container">
    <Nuxt/>
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
    }
}

</script>

<style>
    body{
        background-color: #f8f9fa;
        font-family: 'Nunito', sans-serif;
    }
    

</style>