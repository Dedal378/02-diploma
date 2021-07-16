<template>
  <form @submit.prevent="submit" class="card card-w30">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select v-model="appType" id="type">
        <option value="AppTitle">Заголовок</option>
        <option value="AppSubtitle">Подзаголовок</option>
        <option value="AppAvatar">Аватар</option>
        <option value="AppText">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea
          v-model="value"
          id="value"
          rows="3">
      </textarea>
    </div>

    <button
        class="btn primary"
        :disabled="isValidate"
    >
      Добавить
    </button>
  </form>
</template>

<script>
export default {
  name: "AppForm",
  data() {
    return {
      appType: 'AppTitle',
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

      this.appType = 'AppTitle'
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
