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
      firebaseDatabase: 'https://vue-02-diploma-default-rtdb.europe-west1.firebasedatabase.app/',
      localStorageId: {},
    }
  },
  methods: {
    async loadComments() {
      this.loader = true
      const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await response.json()
      this.loader = false
    },
    async loadResumeData(){
      const { data } = await axios.get(`${ this.firebaseDatabase }resume.json`)

    },
    async addResumeData(userData) {
      const { data } = await axios.post(`${ this.firebaseDatabase }resume.json`, userData)
      this.localStorageId = data
      // this.setLocalStorage()
      this.userData.push(userData)
    },
    getLocalStorage() {
      // eslint-disable-next-line no-empty
      if (localStorage) {

      }
    },
    setLocalStorage() {
      const data = this.localStorageId
      localStorage.setItem(Object.keys('resume-' + data), Object.values(data))
    },
    setId() {
      return new Date().getTime()
    }
  },
}
</script>

<style>

</style>
