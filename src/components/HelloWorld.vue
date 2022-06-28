
<script>
import { ref, toRefs, toRef } from 'vue'
export default {
  props: {
    msg: String,
  },
  // 上下文对象context，可解构{}
  // expose是一个函数，可用于显式限制父组件通过模板 refs访问组件实例时暴露的属性
  setup(props, { emit, expose }) {
    expose()
    const count = ref(0)
    expose({ c: count })
    // 如果需要结构props,或者需要将props传递给外部函数同时保持反应性，可以使用toRefs()和toRef()实用程序 API
    const { msg } = toRefs(props)
    console.log(msg.value)
    const msg1 = toRef(props, 'msg')
    console.log(msg1.value)
    // const emit = defineEmits(['click'])
    const sonClick = () => {
      emit('click')
    }
    return {
      count,
      msg,
      sonClick,
    }
  },
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <div>{{ count }}</div>
  <button type="button" @click="sonClick">按钮</button>
  <p :class="$style.red">
    css模块(生成的类被散列以避免冲突，达到将 CSS 仅作用于当前组件的相同效果)
  </p>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
<style module>
.red {
  color: red;
}
</style>
