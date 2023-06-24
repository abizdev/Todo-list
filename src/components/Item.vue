<template>
  <div class="item">
    <div class="item-top" :class="grid ? '' : 'row'">
      <h3 class="item-top__title">{{ item.title }}</h3>
      <span class="item-top__date">{{ item.date }}</span>
    </div>
    <p class="item-text">{{ item.desc }}</p>
    <div class="item-btn">
      <button class="btn-edit">
        <img src="@/assets/images/change.png" alt="">
        <span>РЕДАКТИРОВАТЬ</span>
      </button>
      <button class="btn-del">
        <img src="@/assets/images/delete.png" alt="">
        <span>Удалить</span>
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['item', 'grid'],
  }
</script>