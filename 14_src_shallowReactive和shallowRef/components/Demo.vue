<template>
  <h4>當前的x.y值是: {{ x.y }}</h4>
  <button @click="x = { y: 888 }">點我替換x</button>
  <button @click="x.y++">點我x.y++</button>
  <hr />
  <h4>{{ person }}</h4>
  <h2>姓名: {{ name }}</h2>
  <h2>年齡: {{ age }}</h2>
  <h2>薪資: {{ job.j1.salary }}k</h2>
  <button @click="name += '~'">點我加波浪符</button>
  <button @click="age++">點我增長歲數</button>
  <button @click="job.j1.salary++">增長薪資</button>
</template>

<script>
import { ref, reactive, toRefs, shallowReactive, shallowRef } from "vue";
export default {
  name: "Demo",

  //數據
  setup() {
    // let person = shallowReactive({  //只考慮第一層數據的響應式
    let person = reactive({
      name: "張三",
      age: 18,
      job: {
        j1: {
          salary: 40,
        },
      },
    });
    let x = shallowRef({
      y: 0,
    });
    console.log("----", x);

    //返回一個對象(常用)
    return {
      person,
      x,

      ...toRefs(person),
    };
  },
};
</script>
