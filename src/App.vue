<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import Foo from './components/Foo.vue'
import { ref, toRefs, reactive, computed, watch } from 'vue'
let value = ref('小明')
let bool = ref(false)
console.log(toRefs())
const count = reactive({
  data: 1,
})
const change = computed(() => {
  return count.data * 2
})

// 监听
watch(
  change,
  (newVal, oldVal) => {
    console.log(newVal)
    console.log(oldVal)
  },
  {
    immediate: true, //立即执行
    deep: true, //深度监听
  }
)
const clickBtn = () => {
  count.data = count.data * 3
  value.value = '小红'
  bool.value = !bool.value
  console.log($refs)
}
</script>

<template>
  <!-- 动态组件 -->
  <component
    :is="bool ? HelloWorld : Foo"
    @click="clickBtn"
    :msg="value"
    ref="comp"
  ></component>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <HelloWorld @click="clickBtn" :msg="value" /> -->
</template>

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
