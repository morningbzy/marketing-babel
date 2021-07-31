<template>
  <el-container>
    <el-aside class="widgets">
      <draggable
        :list="widgetTypes"
        :group="{ name: 'people', pull: 'clone', put: false }"
      >
        <el-card
          v-for="widget in widgetTypes"
          :key="widget.name"
          shadow="hover"
        >
          {{ widget.name }}
        </el-card>
      </draggable>
    </el-aside>
    <el-main>
      <el-card
        shadow="never"
        class="phone"
        :body-style="{ padding: 0, height: '100%' }"
      >
        <draggable :list="x" group="people" class="phone-content">
          <el-card
            v-for="xi in x"
            :key="xi.name"
            shadow="hover"
            body-style="{padding: '0px'}"
          >
            <component :is="xi.component" :haha="xi.name"></component>
          </el-card>
        </draggable>
      </el-card>
    </el-main>
    <el-aside>
      <span>属性</span>
    </el-aside>
  </el-container>
</template>

<script>
import draggable from "vuedraggable";
import TopBanner from "./widgets/TopBanner";
import ImageBox from "./widgets/ImageBox";
import TextBox from "./widgets/TextBox";

export default {
  name: "Page",
  components: {
    draggable,
    TopBanner,
    ImageBox,
    TextBox,
  },
  props: {
    msg: String,
  },
  data() {
    return {
      x: [],
      widgetTypes: [
        {
          name: "顶图",
          component: "TopBanner",
        },
        {
          name: "图片",
          component: "ImageBox",
        },
        {
          name: "文本框",
          component: "TextBox",
        },
      ],
      drag: false,
    };
  },
  methods: {
    log: function (e) {
      window.console.log(e);
    },
  },
};
</script>

<style scoped>
.widgets .el-card {
  margin: 8px;
}

.phone {
  width: 375px;
  height: 660px;
}

.phone .el-card {
  border: 0;
}

.phone-content {
  height: 100%;
}
</style>