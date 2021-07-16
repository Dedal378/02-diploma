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
            :is="app-title"
        ></components>

        <app-title
            :title="title"
         />
        <app-avatar
            :src="avatar"
        />
        <app-subtitle
            :subtitle="subtitle"
        />
        <app-text
            :text="text"
        />

        <h3>Добавьте первый блок, чтобы увидеть результат</h3>
      </div>
    </div>

    <app-comments
        email="test@microsoft.com"
        comment="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eligendi, reiciendis."
    />

  </div>
</template>

<script>
import AppTitle from '@/components/AppTitle'
import AppAvatar from '@/components/AppAvatar'
import AppSubtitle from '@/components/AppSubtitle'
import AppText from '@/components/AppText'

export default {
  components: {
    // eslint-disable-next-line vue/no-unused-components
    AppTitle, AppAvatar, AppSubtitle, AppText,
    'AppComments': () => import('@/components/AppComments')
  },
  data() {
    return {
      title: 'Резюме',
      subtitle: 'Опыт работы',
      avatar: 'https://cdn.dribbble.com/users/5592443/screenshots/14279501/drbl_pop_r_m_rick_4x.png',
      text: 'главный герой американского мультсериала «Рик и Морти», гениальный учёный, изобретатель, атеист (хотя в некоторых сериях он даже молится Богу, однако, каждый раз после чудесного спасения ссылается на удачу и вновь отвергает его существование), алкоголик, социопат, дедушка Морти. На момент начала третьего сезона ему 70 лет[1]. Рик боится пиратов, а его главной слабостью является некий - "Санчезиум". Исходя из того, что существует неограниченное количество вселенных, существует неограниченное количество Риков, герой сериала предположительно принадлежит к измерению С-137. В серии комикcов Рик относится к измерению C-132, а в игре «Pocket Mortys» — к измерению C-123[2]. Прототипом Рика Санчеза является Эмметт Браун, герой кинотрилогии «Назад в будущее»[3].',
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
