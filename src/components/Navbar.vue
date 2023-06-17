<template>
  <nav class="navbar">
    <div class="navbar-nav container" v-if="navbar">
      <button class="navbar-btn btn-lang">Ru</button>
      <h1 class="navbar-nav__title">Заметки</h1>
      <button class="navbar-btn btn-search" @click.prevent="navbar = !navbar">
        <img src="@/assets/images/search.png" alt="search">
      </button>
    </div>
    <div class="navbar-search container" v-else>
      <form class="navbar-search__form">
        <button class="navbar-btn back" @click="navbar = !navbar">
          <img src="@/assets/images/back.svg" alt="">
        </button>
        <input type="text" placeholder="Поиск..." class="navbar-search__input">
        <button class="navbar-btn claer" @click.prevent="">
          <img src="@/assets/images/clear.svg" alt="">
        </button>
      </form>
    </div>
  </nav>
</template>

<script>
  export default {
    data() {
      return {
        navbar: false
      }
    },
  }
</script>