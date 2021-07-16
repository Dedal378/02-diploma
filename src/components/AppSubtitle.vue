<template>
  <h2>
    <slot>
      {{ subtitle }}
    </slot>
  </h2>
</template>

<script>
export default {
  name: "AppSubtitle",
  props: { subtitle: String }
}
</script>

<style scoped>

</style>
