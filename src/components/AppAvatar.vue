<template>
  <div class="avatar">
    <img :src="$attrs.value">
    <!--<slot><img :src="$attrs.value"></slot>-->
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
  height: 150px;
  object-fit: cover;
  border-radius: 50%;
}
</style>
