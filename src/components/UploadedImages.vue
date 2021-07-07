<template>
  <div class="uploaded">
    <div
      class="uploaded__images uploaded__images_empty"
      v-if="images.length === 0"
    >
      <p class="uploaded__message">
        Здесь будут отображаться ваши загруженные файлы
      </p>
    </div>
    <div class="uploaded__images" v-else>
      <UploadedImage :images="images" />
    </div>
  </div>
</template>

<script>
import UploadedImage from "./UploadedImage.vue";
export default {
  props: {
    images: {
      type: Array,
      required: true,
    },
  },
  components: {
    UploadedImage,
  },
};
</script>

<style lang="less" scoped>
.uploaded {
  display: flex;
  align-items: center;
  align-self: normal;
  margin: 0 auto;
  width: 50%;

  &__images {
    display: grid;
    width: 100%;
    align-items: center;
    grid-template-columns: repeat(auto-fill, 150px);
    margin: 30px 0;
    gap: 10px;

    &_empty {
      display: flex;
      align-items: center;
      justify-content: center;
      align-self: normal;
    }
  }
}
</style>
