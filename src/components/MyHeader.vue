<template>
    <nav class="navbar navbar-expand-lg d-flex justify-content-between">
        <div class="h-100 ">
            <img src="/img/spotify.png" alt="" class="h-100 ">
        </div>
        <slot></slot>
    </nav>
</template>

<script>
export default {
  name: 'MyHeader'
}
</script>

<style scoped>

nav{
    background-color: #2e3a46;
    height: 80px;
    width: 100%;
}
</style>
