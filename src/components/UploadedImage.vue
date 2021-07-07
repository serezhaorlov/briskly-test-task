<template>
  <img :src="image" v-for="image in images" :key="image" class="image" />
</template>

<script>
export default {
  props: {
    images: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="less" scoped>
.image {
  width: 100%;
  height: 170px;
}
</style>
