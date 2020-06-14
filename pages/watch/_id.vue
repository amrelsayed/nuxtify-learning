<template>
    <v-container>
        <v-row>
            <v-col md="9" cols="12">
                <div class="video-player-box"
                        ref="videoPlayer"
                        v-video-player:myVideoPlayer="playerOptions">
                        <!-- @ended="markPlayed"> -->
                </div>
            </v-col>
            <v-col md="3" cols="12">
                <div class="display-1">{{ video.name }}</div>

                <div v-html="video.description"></div>

                <span v-for="tag in video.tags" :key="tag.id">
                    <v-btn
                            color="green lighten-2"
                            class="mr-1 mb-2"
                            :to="`/tags/${tag.id}`">
                        {{ tag.name }}
                    </v-btn>
                </span>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import 'video.js/dist/video-js.css'
import Vue from 'vue'
if (process.browser) {
    const VueVideoPlayer = require('vue-video-player/dist/ssr')
    Vue.use(VueVideoPlayer)
}

export default {
    components: {
    },
    head: {
        title: 'Nuxtify Learning - Watch Video'
    },
    async asyncData({ $axios, params }) {
        let video = await $axios.$get(`videos/${params.id}`)
        
        return {
          video
        }
    },
    computed: {
        playerOptions(){
            return {
                language: 'en',
                playbackRates: [0.7, 1.0,1.5, 2.0, 2.5, 3.0],
                sources: [{
                    type: "video/mp4",
                    src: this.video.url
                }],
                poster: this.video.thumb,
                fluid: true
            }
        }
    }
}
</script>