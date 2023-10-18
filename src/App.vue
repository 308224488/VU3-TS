<template>
  <ChuanCanData :title="userName" @click="getName" ref="ChuanCanDataref"></ChuanCanData>
</template>

<script setup lang='ts'>
import { ref, reactive } from 'vue'
import ChuanCanData from './components/10.ChuanCan.vue';

const userName = ref('通过v-bind来实现父子组件传参');
const getName = (name: string) => {
  console.log(name);
}
//使用子组件暴露给子组件的方法和值
const ChuanCanDataref = ref<InstanceType<typeof ChuanCanData>>();
console.log(ChuanCanDataref.value?.name);
//  ChuanCanDataref.value?.requestData();
</script>
<style scoped></style>
