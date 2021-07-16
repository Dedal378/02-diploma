<template>
  <div class="avatar">
    <slot>
      <img :src="$attrs.value">
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
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
