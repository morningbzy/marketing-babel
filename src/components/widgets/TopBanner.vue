<template>
  <div class="top-banner">
    <img :src="require('@/assets/spec/' + imgSrc)" class="top-banner-img"/>
  </div>
</template>

<script>
export default {
  name: "TopBanner",
  components: {},
  props: {
    w: Object,
  },
  data() {
    return {
      imgSrc: "ji_01.jpg",
    };
  },
  computed: {
  }
};
</script>

<style scope>
.top-banner {
  line-height: 0;
}

.top-banner-img {
  width: 100%;
}
</style>