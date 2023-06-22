<template >
  <Transition name="scale">
    <div class="modal" @click="closeModal">
      <div class="modal__content" @click.stop>
        <h4 class="modal__content--title">Добавить заметку</h4>
        <label class="modal__content--input">
          <span>Title</span>
          <input type="text" placeholder="Title" v-model="title">
        </label>
        <label class="modal__content--input">
          <span>Content</span>
          <input type="text" placeholder="Content" v-model="desc">
        </label>
        <div class="modal__content--btns">
          <button class="modal-btn btn-add" @click="closeModal">Отмена</button>
          <button class="modal-btn btn-cancel" @click="addItem">Добавить</button>
        </div>
      </div>
    </div>
  </Transition>
</template>

<script>
export default {
  data() {
    return {
      title: '',
      desc: '',
    }
  },
  methods: {
    closeModal() {
      this.$emit('closeModal', false)
      this.title = ''
      this.desc = ''
    },
    addItem() {
      if(this.title != '' && this.desc != '') {
        const item = {
          id: 1,
          title: this.title,
          desc: this.desc
        }
        this.$emit('addItem', item)
        this.closeModal()
      }
    }
  },
}
</script>