<template >
  <section class="content container">
    <div class="content-top">
      <h2>Все заметки</h2>
      <button class="toggle-btn">
        <img src="@/assets/images/grid.png" alt="">
        <!-- <img src="@/assets/images/list.png" alt=""> -->
        <span> Список<!-- Сетка --></span>
      </button>
    </div>
    <div class="content-items grid">
      <item />
    </div>
  </section>
</template>

<script>
import Item from '@/components/Item.vue'
export default {
  components: {
    Item
  }
}
</script>