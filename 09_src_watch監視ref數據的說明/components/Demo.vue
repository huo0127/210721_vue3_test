<template>
  <h2>當前求和為: {{ sum }}</h2>
  <button @click="sum++">點我加一</button>
  <hr />
  <h2>你好啊{{ msg }}</h2>
  <button @click="msg += '!'">點我加驚嘆號</button>
  <hr />
  <h2>姓名: {{ person.name }}</h2>
  <h2>年齡: {{ person.age }}</h2>
  <h2>薪資: {{ person.job.j1.salary }}k</h2>
  <button @click="person.name += '~'">點我加波浪符</button>
  <button @click="person.age++">點我增長歲數</button>
  <button @click="person.job.j1.salary++">增長薪資</button>
</template>

<script>
import { ref, watch } from "vue";
export default {
  name: "Demo",

  //數據
  setup() {
    let sum = ref(0);
    let msg = ref("你好啊");
    let person = ref({
      name: "張三",
      age: 18,
      job: {
        j1: {
          salary: 40,
        },
      },
    });

    console.log(person);

    watch(sum, (newValue, oldValue) => {
      console.log("sum的值變化了", newValue, oldValue);
    });

    watch(
      person,
      (newValue, oldValue) => {
        console.log("sum的值變化了", newValue, oldValue);
      },
      { deep: true }
    );

    //返回一個對象(常用)
    return {
      sum,
      msg,
      person,
    };
  },
};
</script>
