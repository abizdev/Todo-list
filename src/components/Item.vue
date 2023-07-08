<template>
  <div class="item">
    <div class="item-top" :class="grid ? '' : 'row'">
      <h3 class="item-top__title">{{ item.title }}</h3>
      <span class="item-top__date">{{ item.date }}</span>
    </div>
    <p class="item-text">{{ item.desc }}</p>
    <div class="item-btn">
      <button class="btn-edit" @click="$emit('change-item', item.id)">
        <img src="@/assets/images/change.png" alt="">
        <span>{{ words.editBtn[lang] }}</span>
      </button>
      <button class="btn-del" @click="$emit('del-item', item.id)">
        <img src="@/assets/images/delete.png" alt="">
        <span>{{ words.delBtn[lang] }}</span>
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['item', 'grid', 'lang'],
    inject: ['words'],
  }
</script>