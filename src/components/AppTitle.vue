<template>
  <h1>
    <slot>{{ title }}</slot>
  </h1>
</template>

<script>
export default {
  name: "AppTitle",
  props: { title: String }
}
</script>

<style scoped>

</style>
