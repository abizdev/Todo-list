<template>
  <navbar />
  <content-items />
  <modal v-show="openOrCloseM" @closeModal="closeModal" @addItem="addItem" />
  <add-btn @openModal="openModal" />
</template>

<script>
import Navbar from './components/Navbar.vue';
import ContentItems from './components/Contentitems.vue';
import Modal from './components/Modal.vue';
import AddBtn from './components/AddBtn.vue';

export default {
  components: {
    Navbar,
    ContentItems,
    Modal,
    AddBtn,
  },
  data() {
    return {
      openOrCloseM: false
    }
  },
  methods: {
    openModal(bool) {
      this.openOrCloseM = bool
    },
    closeModal(bool) {
      this.openOrCloseM = bool
    },
    addItem(itemObj) {
      console.log(itemObj);
    }
  },
}
</script>

<style>
  
</style>