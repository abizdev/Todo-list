<template>
  <nav class="navbar">
    <div class="navbar-nav container" v-if="navbar">
      <button class="navbar-btn btn-lang" @click="changeLang" v-if="lang == 'en'">Ru</button>
      <button class="navbar-btn btn-lang" @click="changeLang" v-else>En</button>
      <h1 class="navbar-nav__title">{{ words.navbarTitle[lang] }}</h1>
      <button class="navbar-btn btn-search" @click.prevent="navbar = !navbar">
        <img src="@/assets/images/search.png" alt="search">
      </button>
    </div>
    <div class="navbar-search container" v-else>
      <form class="navbar-search__form">
        <button class="navbar-btn back" @click="navbar = !navbar">
          <img src="@/assets/images/back.svg" alt="">
        </button>
        <input type="text" :placeholder="words.navbarSearch[lang]" class="navbar-search__input" v-model="search">
        <button class="navbar-btn claer" @click.prevent="search = ''">
          <img src="@/assets/images/clear.svg" alt="">
        </button>
      </form>
    </div>
  </nav>
</template>

<script>
  export default {
    props: ['lang'],
    inject: ['words'],
    data() {
      return {
        navbar: true,
        search: ''
      }
    },
    watch: {
      search(val) {
        this.$emit('getSearch', val)
        console.log(val);
      }
    },
    methods: {
      changeLang() {
        this.$emit('changeLang', this.lang == 'ru' ? 'en' : 'ru')
      }
    },
  }
</script>