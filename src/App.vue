<template>
  <div class="wrapper" id="app">
    <div class="container column">
      <app-form @user-data="addResumeData" />
      <app-user-data-view :components="userData" />
    </div>

    <div class="container">
      <app-loader v-if="loader" />
      <app-comments
          v-else
          :comments="comments"
          @load-comments="loadComments"
      />
    </div>
  </div>
</template>

<script>
import AppForm from "@/components/AppForm"
import AppLoader from "@/components/AppLoader"
import AppUserDataView from "@/components/AppUserDataView"
import axios from "axios"

export default {
  components: {
    AppForm, AppLoader, AppUserDataView,
    'AppComments': () => import('@/components/AppComments'),
  },
  data() {
    return {
      value: '',
      userData: [],
      comments: [],
      loader: false,
      firebaseDatabaseLink: 'https://vue-02-diploma-default-rtdb.europe-west1.firebasedatabase.app/',
      localStorageId: '',
    }
  },
  methods: {
    async loadComments() {
      this.loader = true
      const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await response.json()
      this.loader = false
    },
    async loadResumeData() {
      const { data } = await axios.get(`${ this.firebaseDatabaseLink }resume/${ this.localStorageId }.json`)
      if (data) {
        this.userData = Object.keys(data).map(key => {
          return {
            id: key,
            ...data[key]
          }
        })
      }
    },
    async addResumeData(userData) {
      await axios.post(`${ this.firebaseDatabaseLink }resume/${ this.localStorageId }.json`, userData)
      this.setLocalStorage()
      this.userData.push(userData)
    },
    getLocalStorage() {
      this.localStorageId = JSON.parse(localStorage.getItem('resume'))
    },
    setLocalStorage() {
      this.getLocalStorage()
      if (this.localStorageId === '') {
        console.log('set')
        this.localStorageId = this.setId()
        localStorage.setItem('resume', this.localStorageId)
      }
    },
    setId() {
      return new Date().getTime()
    }
  },
  mounted() {
    this.setLocalStorage()
    this.loadResumeData()
  }
}
</script>

<style>

</style>
