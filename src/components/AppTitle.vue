<template>
  <h1>
    {{ $attrs.value }}
    <!--<slot>{{ title }}</slot>-->
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
