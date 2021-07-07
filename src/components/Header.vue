<template>
  <header class="header">
    <h1 class="header__logo">File Uploader</h1>
    <div class="header__box">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<style lang="less" scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 50%;

  &__box {
    display: flex;

    a {
      font-weight: bold;
      color: #2c3e50;
      margin: 0 10px 0 0;
      text-decoration: none;
      &.router-link-exact-active {
        color: #42b983;
      }
    }
  }

  &__logo {
    margin: 0;
  }
}
</style>
