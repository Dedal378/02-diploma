<template>
  <div class="avatar">
    <slot>
      <img :src="src">
    </slot>
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
