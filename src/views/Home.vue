<template>
  <div class="container">
      <router-link to="puzzle" tag="button">Загадки</router-link>
      <router-link to="form" tag="button">Форма</router-link>
  </div>
</template>

<script>
export default {
  name: 'Home'
}
</script>

<style scoped lang="scss">
    .container {
        background-color: white;
        width: 60%;
        height: 60%;
        min-width: 400px;
        max-width: 500px;
        padding: 40px;
        overflow: auto;
        margin: auto;
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        font-size: 18px;
    }
</style>
