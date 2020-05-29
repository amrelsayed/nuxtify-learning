<template>
  <div>
    <nuxt-link :to="`/videos/${video.id}/edit`">
      {{ video.name }}
    </nuxt-link>
  </div>
</template>

<script>
export default {
  props: ['video']
}
</script>

<style>

</style>