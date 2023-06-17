<template>
  <navbar />
  <content-items />
  
  <div class="modal"></div>
  <button class="add-item"></button>
</template>

<script>
import Navbar from './components/Navbar.vue';
import ContentItems from './components/Contentitems.vue';

export default {
  components: {
    Navbar,
    ContentItems
  }
}
</script>

<style>
  
</style>