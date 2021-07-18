<template>
  <div v-if="comments.length" class="card">
    <h2>Комментарии</h2>
    <ul class="list">
      <li
          v-for="comment in comments"
          :key="comment.id"
          class="list-item">
        <div>
          <p><strong>{{ comment.email }}</strong></p>
          <small>{{ comment.body }}</small>
        </div>
      </li>
    </ul>
  </div>

  <p v-else>
    <button @click="loadComments" class="btn primary">
      Загрузить комментарии
    </button>
  </p>
</template>

<script>
export default {
  name: "AppComments",
  emits: {
    // TODO придумать валидацию на комменты
    'load-comments'() {
      console.log('valid')
      return true
    }
  },
  props: {
    comments: {
      type:Array,
      required: true
    }
  },
  methods: {
    loadComments() {
      this.$emit('load-comments')
    }
  },
}
</script>

<style scoped>

</style>
