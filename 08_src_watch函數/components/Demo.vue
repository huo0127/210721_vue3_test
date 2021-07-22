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
import { ref, reactive, watch } from "vue";
export default {
  name: "Demo",

  //數據
  setup() {
    let sum = ref(0);
    let msg = ref("你好啊");
    let person = reactive({
      name: "張三",
      age: 18,
      job: {
        j1: {
          salary: 40,
        },
      },
    });

    //情況一: 監視ref所定義的一個響應式數據
    // watch(
    //   sum,
    //   (newValue, oldValue) => {
    //     console.log("sum變了", newValue, oldValue);
    //   },
    //   { immediate: true }
    // );

    //情況二: 監視ref所定義的多個響應式數據
    watch(
      [sum, msg],
      (newValue, oldValue) => {
        console.log("sum或msg變了", newValue, oldValue);
      },
      { immediate: true }
    );

    /*
      情況三: 監視reactive所定義的一個響應式數據的全部屬性
          1. 注意: 此處無法正確的獲取oldValue
          2. 注意: 強制開啟了深度監視(deep配置無效)
    */
    // watch(person, (newValue, oldValue) => {
    //   console.log("person變化了", newValue, oldValue);
    //  此處deep配置無效
    // },{deep:false});

    //  情況四: 監視reactive所定義的一個響應式數據的某個屬性
    // watch(
    //   () => person.name,
    //   (newValue, oldValue) => {
    //     console.log("person的name變化了", newValue, oldValue);
    //   }
    // );

    //  情況五: 監視reactive所定義的一個響應式數據的某些屬性
    // watch([() => person.name, () => person.age], (newValue, oldValue) => {
    //   console.log("person的name或age變化了", newValue, oldValue);
    // });

    //特殊情況
    // watch(
    //   () => person.job,
    //   (newValue, oldValue) => {
    //     console.log("person的job變化了", newValue, oldValue);
    //   },
    //此處由於監視的是reactive所定義的對象中的某個屬性, 所以deep配置有效
    //   { deep: true }
    // );

    //返回一個對象(常用)
    return {
      sum,
      msg,
      person,
    };
  },
};
</script>
