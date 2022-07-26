<template>
  <section id="musics" class="container mt-5">
    <div class="row">
      <div class="max-5 text-white mb-5" v-for="music in musics" :key="music.title">
        <MusicCard :image="music.poster" :title="music.title" :author="music.author" :anno="music.year"/>
      </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios'
import MusicCard from './MusicCard.vue'
export default {
  name: 'MyMain',
  components: { MusicCard },
  data () {
    return {
      musics: []
    }
  },
  mounted () {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((res) => {
      this.musics = res.data.response
    })
  }
}
</script>

<style scoped>
.max-5{
  width: calc(100%/5);
}
</style>
