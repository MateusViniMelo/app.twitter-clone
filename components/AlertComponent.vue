<template>
    <div :class="`alert alert-${status} text-center`" role="alert">
        {{message}}
    </div>
</template>

<script>
export default {
    name: "AlertComponent",
    props: {
        status:{
            type: String,
            default: ""
        },
        message:{
            type: String,
            default: ""
        }
    }
}
</script>

<style>

</style>