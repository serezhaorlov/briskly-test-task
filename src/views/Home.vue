<template>
  <Header />
  <hr class="hr" />
  <UploadArea @add-image="addImageToArray" @upload="onUpload" />
  <UploadedImages :images="images" />
</template>

<script>
import { defineComponent, ref } from "vue";
import Header from "../components/Header.vue";
import UploadArea from "../components/UploadArea.vue";
import UploadedImages from "../components/UploadedImages.vue";

export default defineComponent({
  name: "App",
  components: {
    Header,
    UploadArea,
    UploadedImages,
  },
  setup() {
    let files = ref([]);
    let images = ref([]);

    const addImageToArray = (file) => {
      if (!file.type.match("image.*")) {
        alert("Перетащите картинку!");
        return;
      }
      const checkOnName = files.value.some(function (e) {
        return e.name === file.name;
      });
      if (checkOnName) {
        alert("Файл с таким именем уже загружен");
        return;
      } else {
        files.value.push(file);

        const reader = new FileReader();
        reader.onload = (e) => {
          images.value.push(e.target.result);
        };
        reader.readAsDataURL(file);
      }
    };

    const onUpload = () => {
      console.log(btoa(files.value));
      images.value = []; /* якобы загружаю на сервер и сбрасываю массивы */
      files.value = [];
    };
    return {
      images,
      onUpload,
      addImageToArray,
    };
  },
});
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
}

.hr {
  width: 50%;
}
</style>
