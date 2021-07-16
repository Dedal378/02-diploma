<template>
  <div class="container">
    <p>
      <button
          class="btn primary"
          @click="loadComments"
      >
        Загрузить комментарии
      </button>
    </p>

    <div class="card">
      <h2>Комментарии</h2>

      <ul class="list">
        <li
            class="list-item"
            v-for="comment in comments"
            :key="comment.id"
        >
          <div>
            <p><strong>{{ comment.email }}</strong></p>
            <small>{{ comment.body }}</small>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppComments",
  emits: ['loadComments'],
  props: { comments: Array },
  methods: {
    loadComments() {
      this.$emit('loadComments')
    }
  },
}
</script>

<style scoped>

</style>
