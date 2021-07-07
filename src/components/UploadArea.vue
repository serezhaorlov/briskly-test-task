<template>
  <div class="upload-area" @dragover.prevent @drop="onDrop">
    <span class="upload-area__message">Перенесите файл сюда!</span>
  </div>
  <button type="button" class="upload-area__button" @click="onUpload">
    Upload
  </button>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup(props, { emit }) {
    let isDragging = ref(false);

    const onDrop = (event) => {
      event.preventDefault();
      event.stopPropagation();
      const files = event.dataTransfer?.files;

      Array.from(files).forEach((file) => {
        emit("add-image", file);
      });

      isDragging.value = false;
    };

    const onUpload = () => {
      emit("upload");
    };

    return {
      onDrop,
      onUpload,
    };
  },
});
</script>

<style lang="less" scoped>
.upload-area {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50%;
  height: 500px;
  border: 1px solid gray;
  border-radius: 20px;
  margin: 30px 0;

  &__form__message {
  }

  &__button {
    width: 150px;
    height: 50px;
    border: none;
    border-radius: 10px;
    color: #42b983;

    &:hover {
      border: 1px solid #42b983;
      cursor: pointer;
    }
  }
}
</style>
