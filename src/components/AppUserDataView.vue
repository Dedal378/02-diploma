<template>
  <div class="card card-w70">
    <components
        v-for="component in components"
        :key="component.id"
        :is="'app-' + component.appType"
        :value="component.value"
    >
    </components>

    <h3 v-if="!components.length">Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>

export default {
  name: "AppUserDataView",
  components: {
    'AppTitle': () => import('@/components/AppTitle'),
    'AppAvatar': () => import('@/components/AppAvatar'),
    'AppSubtitle': () => import('@/components/AppSubtitle'),
    'AppText': () => import('@/components/AppText'),
  },
  props: {
    components: {
      type: Array,
      required: true
    }
  },
}
</script>

<style scoped>

</style>
