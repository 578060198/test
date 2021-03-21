<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>{{count}}</h1>
    <h2>{{double}}</h2>
    <!-- <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
    <button @click="increase">add count +1</button>
  </div>
</template>

<script lang="ts">
import { ref, computed, reactive, toRefs } from 'vue'

interface DataProps {
  count: number,
  increase: () => void,
  double: number
}

export default {
  name: 'App',
  setup() {
    // const count = ref(0)
    // const double = computed(() => {
    //   return count.value * 2
    // })
    // const increase = () => count.value++
    const data: DataProps = reactive({
      count: 0,
      increase: () => {data.count++},
      double: computed(() => data.count * 2)
    })
    const refProps = toRefs(data)
    return {
      ...refProps
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
