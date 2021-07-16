<template>
  <div class="wrapper" id="app">
    <div class="container column">

      <form class="card card-w30">
        <div class="form-control">
          <label for="type">Тип блока</label>
          <select id="type">
            <option value="title">Заголовок</option>
            <option value="subtitle">Подзаголовок</option>
            <option value="avatar">Аватар</option>
            <option value="text">Текст</option>
          </select>
        </div>

        <div class="form-control">
          <label for="value">Значение</label>
          <textarea id="value" rows="3"></textarea>
        </div>

        <button class="btn primary">Добавить</button>
      </form>

      <div class="card card-w70">
        <components
            v-for="component in components"
            :key="component.id"
            :is="component.component"
        >
          {{ component.value }}
        </components>

        <h3 v-if="!components.length">Добавьте первый блок, чтобы увидеть результат</h3>
      </div>
    </div>

    <app-comments
        email="test@microsoft.com"
        comment="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eligendi, reiciendis."
    />

  </div>
</template>

<script>
export default {
  components: {
    // eslint-disable-next-line vue/no-unused-components
    'AppTitle': () => import('@/components/AppTitle'),
    'AppAvatar': () => import('@/components/AppAvatar'),
    'AppSubtitle': () => import('@/components/AppSubtitle'),
    'AppText': () => import('@/components/AppText'),
    'AppComments': () => import('@/components/AppComments'),
  },
  data() {
    return {
      // title: 'Резюме',
      // subtitle: 'Опыт работы',
      // avatar: 'https://cdn.dribbble.com/users/5592443/screenshots/14279501/drbl_pop_r_m_rick_4x.png',
      // text: 'главный герой американского мультсериала «Рик и Морти», гениальный учёный, изобретатель, атеист (хотя в некоторых сериях он даже молится Богу, однако, каждый раз после чудесного спасения ссылается на удачу и вновь отвергает его существование), алкоголик, социопат, дедушка Морти. На момент начала третьего сезона ему 70 лет[1]. Рик боится пиратов, а его главной слабостью является некий - "Санчезиум". Исходя из того, что существует неограниченное количество вселенных, существует неограниченное количество Риков, герой сериала предположительно принадлежит к измерению С-137. В серии комикcов Рик относится к измерению C-132, а в игре «Pocket Mortys» — к измерению C-123[2]. Прототипом Рика Санчеза является Эмметт Браун, герой кинотрилогии «Назад в будущее»[3].',
      components: [
        {
          id: this.id(),
          component: 'AppTitle',
          value: 'Резюме',
          isTrue: false
        },
        {
          id: this.id(),
          component: 'AppSubtitle',
          value: 'Опыт работы',
          isTrue: false
        },
        {
          id: this.id(),
          component: 'AppAvatar',
          value: 'https://cdn.dribbble.com/users/5592443/screenshots/14279501/drbl_pop_r_m_rick_4x.png',
          isTrue: false
        },
        {
          id: this.id(),
          component: 'AppText',
          value: 'главный герой американского мультсериала «Рик и Морти», гениальный учёный, изобретатель, атеист (хотя в некоторых сериях он даже молится Богу, однако, каждый раз после чудесного спасения ссылается на удачу и вновь отвергает его существование), алкоголик, социопат, дедушка Морти. На момент начала третьего сезона ему 70 лет[1]. Рик боится пиратов, а его главной слабостью является некий - "Санчезиум". Исходя из того, что существует неограниченное количество вселенных, существует неограниченное количество Риков, герой сериала предположительно принадлежит к измерению С-137. В серии комикcов Рик относится к измерению C-132, а в игре «Pocket Mortys» — к измерению C-123[2]. Прототипом Рика Санчеза является Эмметт Браун, герой кинотрилогии «Назад в будущее»[3].',
          isTrue: false
        },
      ]
    }
  },
  methods: {
    id() {
      return 'component-' + Math.random()
    }
  },
}
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
