<template>
  <navbar @getSearch="search = $event" :lang="lang" @changeLang="changeLang" />
  <content-items
    :itemList="filterItemList"
    @changeItem="changeItem"
    @delItem="delItem"
    :lang="lang"
  />
  <modal
    v-show="openOrCloseM"
    @closeModal="closeModal"
    @addItem="addItem"
    :currentId="currentId"
    :edit="edit"
    :itemObj="itemObj"
    @editItem="editItem"
    :lang="lang"
  />
  <add-btn @openModal="openModal" />
</template>

<script>
import Navbar from "./components/Navbar.vue";
import ContentItems from "./components/Contentitems.vue";
import Modal from "./components/Modal.vue";
import AddBtn from "./components/AddBtn.vue";
import langs from "@/lang.js";

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
      edit: false,
      currentId: 1,
      itemList: [],
      itemObj: {},
      search: "",
      lang: "ru",
      langWords: {},
    };
  },
  computed: {
    filterItemList() {
      return this.search
        ? this.itemList.filter((item) =>
            item.title.toLowerCase().includes(this.search.toLowerCase())
          )
        : this.itemList;
    },
  },
  methods: {
    changeLang(value) {
      this.lang = localStorage.lang = value;
    },
    openModal(bool) {
      this.openOrCloseM = bool;
      this.edit = false;
    },
    closeModal(bool) {
      this.openOrCloseM = bool;
    },
    addItem(itemObj) {
      this.itemList.push(itemObj);
    },
    changeItem(id) {
      this.edit = this.openOrCloseM = true;
      let obj = this.itemList.find((item) => item.id == id);
      this.itemObj = obj;
    },
    delItem(id) {
      this.itemList = this.itemList.filter((item) => item.id != id);
    },
    editItem(obj) {
      this.itemList.forEach((item) => {
        if (item.id == obj.id) {
          item.title = obj.title;
          item.desc = obj.desc;
          item.date = obj.date;
        }
      });
    },
  },
  created() {
    if (localStorage.list) {
      const localList = localStorage.getItem("list");
      this.itemList = JSON.parse(localList);

      if (this.itemList.length >= 1) {
        this.currentId = this.itemList[this.itemList.length - 1].id;
        this.currentId++;
      }
    }
  },
  beforeCreate() {
    if (!localStorage.lang) {
      localStorage.setItem("lang", "ru");
    }

    this.lang = localStorage.lang || "ru";
    this.langWords = langs;
    localStorage.words = JSON.stringify(this.langWords);
  },
  watch: {
    itemList: {
      handler(updateList) {
        console.log(updateList);
        localStorage.setItem("list", JSON.stringify(this.itemList));
      },
      deep: true,
    },
  },
  provide() {
    return {
      words: JSON.parse(localStorage.words),
    };
  },
};
</script>

<style></style>
