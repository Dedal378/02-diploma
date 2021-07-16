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
        <li class="list-item">
          <div>
            <p><strong>{{ email }}</strong></p>
            <small>{{ comment }}</small>
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
  props: {
    email: String,
    comment: String,
  },
  methods: {
    loadComments() {
      this.$emit('loadComments')
    }
  },
}
</script>

<style scoped>

</style>
