<template>
  <v-layout column>
    <v-flex xs6 offset-xs3>
      <panel>
        <slot title="Songs">
          <div v-for="song in songs" :key="song.id">
              {{song.title}}
              {{song.artist}}
              {{song.album}}
            hello
          </div>
        </slot>
      <panel/>
    </v-flex>
  </v-layout>
</template>

<script>
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'
export default {
  components: {
    Panel
  },
  data () {
    return {
    songs: null
    }
  },
  async mounted () {
    this.songs = await (SongsService.index()).data
  }
}
</script>

<style scoped>
</style>
