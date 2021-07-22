<template>
  <h4>{{ person }}</h4>
  <h2>姓名: {{ name }}</h2>
  <h2>年齡: {{ age }}</h2>
  <h2>薪資: {{ job.j1.salary }}k</h2>
  <button @click="name += '~'">點我加波浪符</button>
  <button @click="age++">點我增長歲數</button>
  <button @click="job.j1.salary++">增長薪資</button>
</template>

<script>
import { reactive, toRef, toRefs } from "vue";
export default {
  name: "Demo",

  //數據
  setup() {
    let person = reactive({
      name: "張三",
      age: 18,
      job: {
        j1: {
          salary: 40,
        },
      },
    });
    // const name1 = person.name;
    // console.log(name1);

    // const name2 = toRef(person, "name");
    // console.log(name2);

    const x = toRefs(person);
    console.log("@@", x);

    //返回一個對象(常用)
    return {
      person,
      // name: toRef(person, "name"),
      // age: toRef(person, "age"),
      // salary: toRef(person.job.j1, "salary"),

      ...toRefs(person),
    };
  },
};
</script>
