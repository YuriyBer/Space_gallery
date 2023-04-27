<template>
  <figure
    v-if="item.media_type == 'image'"
    class="gallery__card"
    @click="showModal"
    @pointerenter="hover = true"
    @pointerleave="hover = false"
  >
    <img :src="item.url" alt="" class="gallery__card__img" />
    <figcaption class="gallery__card__capt" v-if="hover">
      <p class="gallery__card__capt__description">{{ item.title }}</p>
    </figcaption>
  </figure>
  <ModalImg
    v-if="item.media_type == 'image'"
    v-show="isModalVisible"
    @close="closeModal"
    :item="item"
  />
  <div class="gallery__card__unknown" v-else>unknown media type event here</div>
</template>

<script>
// import Data from './data.json';
import ModalImg from "./ModalImg.vue";

// console.log(Data.description, Data.image);

export default {
  name: "PhotoCard",
  data() {
    return {
      // photos: Data,
      isModalVisible: false,
      hover: false,
    };
  },
  components: {
    ModalImg,
  },
  methods: {
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
  },
  props: {
    item: Object,
  },
  beforeMount() {
    console.log(this.item);
  },
};
</script>

<style lang="stylus">
.gallery__card
  height 200px
  border 1px solid #ccc
  border-radius 8px
  overflow hidden
  box-shadow: 8px 8px 8px 3px rgba(0, 0, 0, 0.12)
  position relative
  &__img
      max-height 100%
      max-width 100%
  &__capt
      position absolute
      top 0
      background rgba(200,200,255,0.7)
      width 100%
      height 100%
      display flex
      align-items center
      justify-content center
      opacity 1
    &__unknown
      display none
.svg-card
    width 200px
</style>
