<script setup>
// 父向子传参
defineProps({
  msg: String,
})
const msghello = 'Hello!'
const emit = defineEmits(['click'])
const sonClick = () => {
  emit('click')
}
</script>
<template>
  <h1>{{ msg }}</h1>
  <button @click="sonClick">{{ msghello }}</button>
</template>