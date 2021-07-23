<template>
  <h4>當前求和為 {{ sum }}</h4>
  <button @click="sum++">點我++</button>
  <hr />
  <h2>姓名: {{ name }}</h2>
  <h2>年齡: {{ age }}</h2>
  <h2>薪資: {{ job.j1.salary }}k</h2>
  <button @click="name += '~'">點我加波浪符</button>
  <button @click="age++">點我增長歲數</button>
  <button @click="job.j1.salary++">增長薪資</button>
</template>

<script>
import { ref, reactive, toRefs, readonly, shallowReadonly } from "vue";
export default {
  name: "Demo",

  //數據
  setup() {
    let sum = ref(0);
    let person = reactive({
      name: "張三",
      age: 18,
      job: {
        j1: {
          salary: 40,
        },
      },
    });

    // person = readonly(person);
    // person = shallowReadonly(person);
    // sum = readonly(sum);
    // sum = shallowReadonly(sum);

    //返回一個對象(常用)
    return {
      sum,
      ...toRefs(person),
    };
  },
};
</script>
