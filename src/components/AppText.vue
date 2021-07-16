<template>
  <p>
    <slot>{{ text }}</slot>
  </p>
</template>

<script>
export default {
  name: "AppText",
  props: { text: String }
}
</script>

<style scoped>

</style>
