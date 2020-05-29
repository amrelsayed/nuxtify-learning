<template>
  <div>
      <h1>Edit {{ video.name }}</h1>
      <nuxt-link :to="`/videos/${video.id}`">
        Go Back
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