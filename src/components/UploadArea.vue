<template>
  <div
    class="upload-area"
    @dragover.prevent
    @drop="onDrop"
    @dragenter="onEnter"
    @dragleave="onLeave"
    :class="{ draggin: isDragging }"
  >
    <span class="upload-area__message" :class="{ draggin: isDragging }">{{
      isDragging ? "Бросайте!" : " Перенесите файл"
    }}</span>
  </div>
  <button type="button" class="upload-area__button" @click="onUpload">
    Загрузить
  </button>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  emits: ["add-image", "upload"],
  setup(props, { emit }) {
    let isDragging = ref(false);

    let counterFoClassChange = ref(0);

    const onDrop = (event) => {
      event.preventDefault();
      event.stopPropagation();
      const files = event.dataTransfer?.files;

      Array.from(files).forEach((file) => {
        emit("add-image", file);
      });

      isDragging.value = false;
    };

    const onEnter = (e) => {
      e.preventDefault();
      counterFoClassChange.value++;
      isDragging.value = true;
    };

    const onLeave = (e) => {
      e.preventDefault();

      counterFoClassChange.value--;

      if (counterFoClassChange.value <= 0) {
        isDragging.value = false;
      }
    };

    const onUpload = () => {
      emit("upload");
    };

    return {
      onDrop,
      onUpload,
      onEnter,
      onLeave,
      isDragging,
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

  &__message {
    border: 2px dashed red;
    border-radius: 20px;
    padding: 30px;
    width: 200px;
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

.draggin {
  border: 2px dashed #42b983;
}
</style>
