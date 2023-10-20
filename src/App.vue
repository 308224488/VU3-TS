<template>
  <chaCaoData>
    <template v-slot:header>
      <div>
        具名插槽 从父组件向子组件插入内容
      </div>
    </template>
    <template v-slot:footer="{ data, index }">
    {{ index }} --- {{ data.name }} 
    </template>
  </chaCaoData>
</template>

<script setup lang='ts'>
import { ref, reactive, onMounted } from 'vue'
import chaCaoData from './components/12.chaCao.vue';


</script>
<style scoped></style>
