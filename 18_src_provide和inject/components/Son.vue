<template>
  <div class="son">
    <h3>我是Son組件(子), {{ car.name }}---{{ car.price }}</h3>
  </div>
</template>

<script>
import { inject } from "vue";
export default {
  name: "son",
  setup() {
    let car = inject("car");
    console.log(car, "----");
    return { car };
  },
};
</script>

<style>
.son {
  background-color: orange;
  padding: 10px;
}
</style>
