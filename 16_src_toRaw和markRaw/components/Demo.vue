<template>
  <h4>當前求和為 {{ sum }}</h4>
  <button @click="sum++">點我++</button>
  <hr />
  <h2>姓名: {{ name }}</h2>
  <h2>年齡: {{ age }}</h2>
  <h2>薪資: {{ job.j1.salary }}k</h2>
  <h2 v-show="person.car">車輛訊息 {{ person.car }}</h2>
  <button @click="name += '~'">點我加波浪符</button>
  <button @click="age++">點我增長歲數</button>
  <button @click="job.j1.salary++">增長薪資</button>
  <button @click="showRawPerson">原始person數據</button>
  <button @click="addCar">給人添加一台車</button>
  <button @click="person.car.name += '!'">換車名</button>
  <button @click="changePrice">換價格</button>
</template>

<script>
import { ref, reactive, toRefs, toRaw, markRaw } from "vue";
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
    function showRawPerson() {
      const p = toRaw(person);
      p.age++;
      console.log(p);
    }

    function addCar() {
      let car = { name: "mb", price: 40 };
      person.car = markRaw(car);
    }

    function changePrice() {
      person.car.price++;
      console.log(person.car.price);
    }
    //返回一個對象(常用)
    return {
      sum,
      person,
      ...toRefs(person),
      showRawPerson,
      addCar,
      changePrice,
    };
  },
};
</script>
