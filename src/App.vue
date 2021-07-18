<template>
  <div class="wrapper" id="app">
    <div class="container column">
      <app-form @user-data="addData" />
      <app-user-data-view :components="components" />
    </div>

    <div class="container">
      <app-loader v-if="loader" />
      <app-comments
          v-else
          @load-comments="loadComments"
          :comments="comments"
      />
    </div>
  </div>
</template>

<script>
import AppForm from "@/components/AppForm"
import AppLoader from "@/components/AppLoader"
import AppUserDataView from "@/components/AppUserDataView"

export default {
  components: {
    AppForm, AppLoader, AppUserDataView,
    'AppComments': () => import('@/components/AppComments'),
  },
  data() {
    return {
      value: '',
      components: [],
      comments: [],
      loader: false,
    }
  },
  methods: {
    async loadComments() {
      this.loader = true
      const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await response.json()
      this.loader = false
    },
    addData(data) {
      this.components.push(data)
    }
  },
}
</script>

<style>

</style>
