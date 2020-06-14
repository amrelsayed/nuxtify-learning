
<template>
  <div>
    <h1 class="display-3 ma-4 d-flex justify-center">
      Videos with Tag "{{ tag.name }}"
    </h1>

    <div class="d-flex flex-wrap">
      <div v-for="video in videos" :key="video.id">
        <videocard :video="video"></videocard>
      </div>
    </div>
  </div>
</template>

<script>
import videocard from '@/components/VideoCard'
  export default {
    components: {
      videocard
    },
    async asyncData({ $axios, params }) {
        let videos = await $axios.$get(`videos`)
        let tag = await $axios.$get(`tag/${params.id}`)

        return {
          videos,
          tag
        }
    }
  }
</script>

<style lang="scss" scoped>
</style>