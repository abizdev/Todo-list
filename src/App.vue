<template>
  <navbar />
  <content-items :itemList="itemList" />
  <modal 
    v-show="openOrCloseM" 
    @closeModal="closeModal" 
    @addItem="addItem" 
    :currentId="currentId"
  />
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
      openOrCloseM: false,
      currentId: 1,
      itemList: []
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
      this.itemList.push(itemObj)
      console.log(this.itemList);
    },
  },
  created() {
    if(localStorage.list) {
        const localList = localStorage.getItem('list')
        this.itemList = JSON.parse(localList)
        
        if(this.itemList.length >= 1) {
          this.currentId = this.itemList[this.itemList.length - 1].id
          this.currentId++
        }
      }
  },
  watch: {
    itemList: {
      handler(updateList) {
        console.log(updateList);
        localStorage.setItem('list', JSON.stringify(this.itemList))
      },
      deep: true
    }
  }
}
</script>

<style>
  
</style>