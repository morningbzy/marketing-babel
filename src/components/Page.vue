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
    <el-aside width="500px">
      <el-card shadow="never" class="phone">
        <draggable :list="widgets" group="people" class="phone-content">
          <div
            v-for="(w, idx) in widgets"
            :key="`widget-${idx}`"
            shadow="hover"
            @click="onWidgetSelect(idx)"
            class="widget-card"
          >
            <component :is="w.component" :w="w" :selected="editing == `widget-${idx}`"></component>
          </div>
        </draggable>
      </el-card>
    </el-aside>
    <el-main>
      <span>属性</span>
    </el-main>
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
      editing: '',
      widgets: [],
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
  computed: {
  },
  methods: {
    onWidgetSelect: function (idx) {
      this.editing = `widget-${idx}`;
    },
  },
};
</script>

<style scoped>
.widgets .el-card {
  margin: 8px;
}

.phone {
  width: 415px;
  height: 700px;
  margin: 0 auto;
  overflow: auto;
}

.phone .el-card {
  border: 0;
}

.phone-content {
  min-height: 100px;
  height: 100%;
}

.widget-card {
  position: relative;
  transition: 0.3s;
}

.widget-card [selected]::before {
  content: '';
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(64 158 255 / 50%);
}


.widget-card:hover {
  box-shadow: 0 2px 12px 0 rgb(0 0 0 / 50%);
}
</style>