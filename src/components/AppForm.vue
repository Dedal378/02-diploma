<template>
  <form class="card card-w30" @submit.prevent="submit">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select v-model="appType" id="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea v-model="value" id="value" rows="3"></textarea>
    </div>

    <button :disabled="isValidate" class="btn primary">
      Добавить
    </button>
  </form>
</template>

<script>
export default {
  name: "AppForm",
  emits: ['user-data'],
  data() {
    return {
      appType: 'title',
      value: '',
    }
  },
  methods: {
    id() {
      return 'component-' + Math.random()
    },
    submit() {
      this.$emit('userData', {
        id: this.id(),
        value: this.value,
        appType: this.appType,
      })

      this.appType = 'title'
      this.value = ''
    }
  },
  computed: {
    isValidate() {
      if (this.value.length > 3) {
        return false
      }
      return true
    }
  },
}
</script>

<style scoped>

</style>
