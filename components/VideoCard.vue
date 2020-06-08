<template>
    <v-card max-width="340px" 
    hover 
    class="ma-2">
    <!-- :to="{ name: 'video-watch', params: {id: video.id }}"> -->
    <v-img :src="video.thumb" />
    <v-card-title>{{ video.name }}</v-card-title>
    <v-card-text>
        <!-- <div class="green--text" v-if="isPlayed(video.id)">
            <font-awesome-icon icon="check" /> Played
        </div> -->
    </v-card-text>

    <v-card-actions>
        <span v-for="tag in video.tags" :key="`${video.id}-${tag.id}`">
            <v-btn color="green lighten-2"
            class="mr-2"
            small
            @mousedown.stop
            :to="{ name: 'tag', params: {id: tag.id}}">
            {{ tag.name }}
            </v-btn>
        </span>
    </v-card-actions>
    </v-card>

</template>
<script>
export default {
    props: ['video']
}
</script>