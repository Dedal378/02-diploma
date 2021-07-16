<template>
  <div class="avatar">
    <img :src="src">
  </div>
</template>

<script>
export default {
  name: "AppAvatar",
  props: { src: String },
}
</script>

<style scoped>

</style>
