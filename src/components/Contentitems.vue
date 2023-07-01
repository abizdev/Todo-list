<template >
  <section class="content container">
    <div class="content-top">
      <h2>Все заметки</h2>
      <button class="toggle-btn" @click.prevent="grid = !grid">
        <img src="@/assets/images/grid.png" alt="grid" v-if="!grid">
        <img src="@/assets/images/list.png" alt="list" v-else>
        <span>{{ !grid ? 'Сетка' : 'Список'}}</span>
      </button>
    </div>
    <div class="content-items" :class="!grid ? 'flex': 'grid'">
      <item 
        v-for="(item, key) in itemList"  :key="key"
        :item="item"
        :grid="grid"
        @changeItem="$emit('change-item', item.id)"
        @delItem="$emit('del-item', item.id)"
      />
    </div>
  </section>
</template>

<script>
import Item from '@/components/Item.vue'
export default {
  components: { Item },
  props: ['itemList'],
  data() {
    return {
      grid: true
    }
  },
}
</script>