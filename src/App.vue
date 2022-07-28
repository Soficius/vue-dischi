<template>
  <div>
    <MyHeader>
      <MySelect v-model="curGenre" :options="filteredGenres" placeholder="Scegli Una Song" />
    </MyHeader>
    <MyMain>
      <div class="max-5 text-white mb-5" v-for="music in filteredMusic" :key="music.title">
        <MusicCard :image="music.poster" :title="music.title" :author="music.author" :anno="music.year" />
      </div>
    </MyMain>
  </div>
</template>

<script>
import axios from 'axios'
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue'
import MusicCard from './components/MusicCard.vue'
import MySelect from './components/MySelect.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain,
    MusicCard,
    MySelect
  },
  data () {
    return {
      musics: [],
      curGenre: ''
    }
  },
  computed: {
    filteredGenres () {
      const genres = []
      this.musics.forEach((music) => {
        if (!genres.includes(music.genre)) {
          genres.push(music.genre)
        }
      })
      return genres.map((genre, i) => ({
        key: 'genre_' + i,
        value: genre.toLowerCase(),
        desc: genre
      }))
    },
    filteredMusic () {
      if (this.curGenre === '') return this.musics
      return this.musics.filter((music) => music.genre.toLowerCase() === this.curGenre)
    }
  },
  mounted () {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((res) => {
      this.musics = res.data.response
    })
  }
}
</script>

<style lang="scss">
@import './assets/sass/style.scss';
.max-5 {
  width: calc(100%/5);
}
</style>
