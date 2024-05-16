<template>
  <div class="scroll">
    <div>默认配置</div>
    <vue3-seamless-scroll :list="list" :ease="ease" @scroll="onCount" :singleHeight="30" :singleWaitTime="1000">
      <div ref="itemRef" class="item" v-for="(item, index) in list" :key="index">
        <span>{{ item.title }}</span>
        <span>{{ item.date }}</span>
      </div>
    </vue3-seamless-scroll>
  </div>
</template>
<script lang="ts">
const listData = [
  {
    title: "Vue3.0 无缝滚动组件展示数据第 1 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 2 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 3 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 4 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 5 条",
    date: Date.now(),
  },
];
const listData1 = [
  {
    title: "Vue3.0 无缝滚动组件展示数据第 1 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 2 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 3 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 4 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 5 条",
    date: Date.now(),
  },
];
const listData2 = [
  {
    title: "Vue3.0 无缝滚动组件展示数据第 1 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 2 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 3 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 4 条",
    date: Date.now(),
  },
  {
    title: "Vue3.0 无缝滚动组件展示数据第 5 条",
    date: Date.now(),
  },
];
import { defineComponent, ref, onMounted } from "vue";
import { Vue3SeamlessScroll } from "../package/index";

export default defineComponent({
  name: "App",
  components: {
    Vue3SeamlessScroll,
  },
  setup() {
    const list = ref(listData);
    const list1 = ref(listData1);
    const list2 = ref(listData2);
    const syacList = ref();
    const scroll = ref(false);
    const count = ref(1);
    const ease = ref({
      x1: 0,
      y1: 0,
      x2: 1,
      y2: 1,
    });
    const height = ref(500);
    let timer1: NodeJS.Timer;

    let itemRef = ref(null);
    function onCount(num) {
      if (document.getElementsByClassName("item")) {
        for (let index = 0; index < document.getElementsByClassName("item").length; index++) {
          document.getElementsByClassName("item")[index].style.color = "";
        }
        document.getElementsByClassName("item")[num].style.color = "red";
      }

      // console.log(num);
      // if (num === count.value) {
      //   setTimeout(() => {
      //     count.value = num + 1;
      //   }, 2000);
      // }
    }

    return {
      list,
      list1,
      list2,
      syacList,
      scroll,
      count,
      onCount,
      ease,
      height,
    };
  },
});
</script>
<style>
.singleLine {
  display: flex;
  flex-direction: row;
  height: 40px;
  width: 100%;
  overflow: hidden;
  position: relative;
}

.singleLine span {
  display: inline-block;
  height: 20px;
  margin-top: 12px;
  white-space: nowrap;
}

.scroll {
  display: inline-block;
  height: 180px;
  width: 390px;
  margin: 0 25px;
  overflow: hidden;
  position: relative;
}

.scroll > div:first-child {
  font-weight: bold;
  color: red;
  text-align: center;
}

.scroll > div:last-child {
  margin-top: 15px;
  height: 260px;
  overflow: hidden;
}

.scroll .item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  height: 30px;
}

* {
  margin: 0;
  padding: 0;
}
</style>
