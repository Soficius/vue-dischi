<template>
  <div>
    <MyHeader>
      <MySelect
        v-model="curGenre"
        :options="genres"
        :showEmpty="true"
        labelEmpty="Scegli Una Song"
      />
    </MyHeader>
    <MyMain>
      <div class="max-5 text-white mb-5" v-for="music in musics" :key="music.title">
        <MusicCard
          :image="music.poster"
          :title="music.title"
          :author="music.author"
          :anno="music.year"
        />
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
      genres: [],
      curGenre: ''
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
