<template>
  <div class="modal-back" @click="close">
    <div class="modal" role="dialog">
      <figure class="modal-content">
        <img v-bind:src="item.url" class="modal-img" alt="" />
        <figcaption class="modal-caption">
          <h2 class="modal-title">{{ item.title }}</h2>
          <p class="modal-description">{{ item.explanation }}</p>
        </figcaption>
      </figure>
    </div>
  </div>
</template>
<script>
export default {
  name: "ModalImg",
  methods: {
    close() {
      this.$emit("close");
    },
  },
  props: {
    item: Object,
  },
};
</script>
<style lang="stylus">
.modal
    background-color #FFFFFF
    box-shadow 2px 2px 20px 1px #0088FF
    overflow-y: auto
    position relative
    &-back
        position fixed
        top 0
        bottom 0
        left 0
        right 0
        background-color rgba(0, 0, 0, 0.5)
        display flex
        justify-content center
        overflow-y auto
        padding 10px 10%
        z-index 100
    &-img
        max-height 90vh
        max-width 100%
    &-content
        display flex
        flex-direction column
        gap 20px
    &-caption
        display flex
        flex-direction column
        gap 20px
</style>
