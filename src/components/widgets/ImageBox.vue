<template>
  <div class="image-box">
    <img :src="require('@/assets/spec/' + imgSrc)" class="image-box-img"/>
  </div>
</template>

<script>
export default {
  name: "ImageBox",
  components: {},
  props: {
    haha: String,
  },
  data() {
    return {
      imgSrc: "ji_02.jpg",
    };
  },
};
</script>

<style scope>
.image-box {
  line-height: 0;
}

.image-box-img {
  width: 100%;
}
</style>