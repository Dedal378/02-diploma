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
      <textarea id="value" rows="3" v-model.trim="value"></textarea>
    </div>

    <button :disabled="isValidate" class="btn primary">
      Добавить
    </button>
    <!--{{ payload }}-->
  </form>
</template>

<script>
export default {
  name: "AppForm",
  emits: {
    // TODO придумать валидацию на форму, не выводится consoe.log, оно вообще работает?
    'user-data'(payload) {
      this.payload = payload
      console.log('valid', payload)
      return true
    }
  },
  data() {
    return {
      appType: 'title',
      value: '',
      payload: []
    }
  },
  methods: {
    id() {
      return 'component-' + Math.random()
    },
    submit() {
      this.$emit('user-data', {
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
