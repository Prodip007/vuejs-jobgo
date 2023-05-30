<script setup>
</script>

<template>
  <main class="login-page">
    <section class="header">
      <div class="header__logo"></div>
      <h1 class="header__heading">Logo</h1>
    </section>
    <section class="form-section">
      <form class="login-form" action="" method="get">
        <h2  class="login-form__header">Log in</h2>
        <label class="login-form__username-label" for="username">User name</label>
        <input class="login-form__username-input" type="text" name="user" id="">
        <router-link :to="{ name: 'message-board' }" class="login-form__submit-button">Login</router-link>
      </form>
    </section>
    
  </main>
</template>

<style lang="scss" src="../assets/css/views/HomeView.scss">
  
</style>
