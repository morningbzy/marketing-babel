<template>
  <el-container>
    <el-aside>
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
      <el-card shadow="never" class="phone">
        <draggable :list="x" group="people">
          <div v-for="xi in x" :key="xi.name" shadow="hover">
            {{ xi.name }}
          </div>
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

export default {
  name: "Page",
  components: {
    draggable,
  },
  props: {
    msg: String,
  },
  data() {
    return {
      x: [
        {
          name: "顶图",
        },
      ],
      widgetTypes: [
        {
          name: "顶图",
        },
        {
          name: "图片",
        },
        {
          name: "文本框",
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
.el-card {
  margin: 8px;
}

.phone {
    width: 375px;
    height: 660px;
}
</style>