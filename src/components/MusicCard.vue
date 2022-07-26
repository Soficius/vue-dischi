<template>
<div class="music-card text-center p-2 bg-grey h-100">
    <img :src="image" :alt="title" class="img-fluid">
    <h5 class="title">{{title}}</h5>
    <div class="author">{{author}}</div>
    <div class="anno">{{anno}}</div>

</div>

</template>

<script>
export default {
  name: 'MusicCards',
  props: {
    image: String,
    title: String,
    author: String,
    anno: String

  }
}
</script>

<style lang="scss" scoped>

.bg-grey{
    background-color: #2e3a46;
}
</style>
