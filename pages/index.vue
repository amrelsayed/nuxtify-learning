<template>
    <div class="home">
        <div class="display-2 ma-4 d-flex justify-center">
          All Videos
        </div>

        <div class="d-flex flex-wrap">
          <div v-for="video in videos" :key="video.id">
            <videocard :video="video"></videocard>
          </div>
        </div>
    </div>
</template>

<script>
import videocard from '../components/VideoCard'
export default {
  components: {
    videocard
  },
    head: {
        title: 'Nuxtify Learning - Home'
    },
    async asyncData({ $axios }) {
        let videos = await $axios.$get(`videos`)
        
        return {
          videos
        }
    }
}
</script>

<style>

</style>
