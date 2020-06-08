<template>
  <nuxt-child :video="video"></nuxt-child>
</template>

<script>
import {mapState} from 'vuex'
export default {
    head() {
        return {
            title: `${this.video.name} - Nuxtify Learning`
        }
    },
    async fetch({ $axios, params, store }) {
        let video = await $axios.$get(`videos/${params.id}`)
        store.commit('SET_CURRENT_VIDEO', video)
    },
    computed: {
        ...mapState({
            video: 'currentVideo'
        })
    }
}
</script>

<style>

</style>