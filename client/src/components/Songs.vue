<template>
  <v-layout column>
    <v-flex xs6 offset-xs3>
      <panel title="Songs">
          <v-btn slot="action" @click="navigateTo({name: 'songs-create'})" fab light medium absolute right middle class="cyan accent-2">
            <v-icon>add</v-icon>
          </v-btn>

        <div v-for="song in songs" class="song" :key="song.id">
          {{song.title}} - 
          {{song.artist}} - 
          {{song.album}}
        </div>
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
  methods: {
    navigateTo (route) {
      this.$router.push()
    }
  },
  async mounted () {
    this.songs = await (SongsService.index()).data
  }
}
</script>

<style scoped>
</style>
