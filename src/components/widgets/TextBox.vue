<template>
  <div class="text-box">
    <div class="title">TITLE</div>
    <div class="content">{{ haha }}text</div>
  </div>
</template>

<script>
export default {
  name: "TextBox",
  components: {},
  props: {
    haha: String,
  },
  data() {
    return {
    };
  },
};
</script>

<style scope>
.text-box {
  padding: 1em;
}
</style>