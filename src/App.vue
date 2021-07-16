<template>
  <div class="wrapper" id="app">
    <div class="container column">
      <app-form @userData="addData" />
      <app-user-data-view :components="components" />
    </div>

    <div class="container">
      <app-loader v-if="loader" />
      <app-comments
          v-else
          @loadComments="loadComments"
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
      components: [
        // {
        //   id: this.id(),
        //   component: 'AppTitle',
        //   value: 'Резюме',
        // },
        // {
        //   id: this.id(),
        //   component: 'AppSubtitle',
        //   value: 'Опыт работы',
        // },
        // {
        //   id: this.id(),
        //   component: 'AppAvatar',
        //   value: 'https://cdn.dribbble.com/users/5592443/screenshots/14279501/drbl_pop_r_m_rick_4x.png',
        // },
        // {
        //   id: this.id(),
        //   component: 'AppText',
        //   value: 'главный герой американского мультсериала «Рик и Морти», гениальный учёный, изобретатель, атеист (хотя в некоторых сериях он даже молится Богу, однако, каждый раз после чудесного спасения ссылается на удачу и вновь отвергает его существование), алкоголик, социопат, дедушка Морти. На момент начала третьего сезона ему 70 лет[1]. Рик боится пиратов, а его главной слабостью является некий - "Санчезиум". Исходя из того, что существует неограниченное количество вселенных, существует неограниченное количество Риков, герой сериала предположительно принадлежит к измерению С-137. В серии комикcов Рик относится к измерению C-132, а в игре «Pocket Mortys» — к измерению C-123[2]. Прототипом Рика Санчеза является Эмметт Браун, герой кинотрилогии «Назад в будущее»[3].',
        // },
      ],
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
