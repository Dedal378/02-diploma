<template>
  <div class="container">
    <p>
      <button class="btn primary">Загрузить комментарии</button>
    </p>

    <div class="card">
      <h2>Комментарии</h2>

      <ul class="list">
        <li class="list-item">
          <div>
            <p><strong>{{ email }}</strong></p>
            <small>{{ comment }}</small>
          </div>
        </li>
      </ul>
    </div>

    <!--<div class="loader"></div>-->
  </div>
</template>

<script>
export default {
  name: "AppComments",
  props: {
    email: String,
    comment: String,
  }
}
</script>

<style scoped>

</style>
