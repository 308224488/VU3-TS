<template>
    <div>{{ data1 }}</div>
    <button @click="change">通过toRef来改变</button>
    <button @click="change2">通过toRefs来改变</button>
    <button @click="change3">toRaw的作用</button>
</template>

<script setup lang='ts' name="toReftoRefstoRaw">
import { ref, reactive, toRef, toRefs, toRaw } from 'vue'

// toref 只能修改响应式对象的值 非响应式试图毫无变化
const data1 = reactive({
    name: 'toRef',
    age: 18,
});
const data2 = toRef(data1, 'name');
const data3 = toRefs(data1);
const change = () => {
    data2.value = '改变toRef的值';
}
const change2 = () => {
    data3.name.value = "通过toRefs来改变";
}
const change3 = () => {
    // 接收一个代理对象，返回其原始对象。
    console.log(data1);
    console.log(toRaw(data1));
}
</script>
<style scoped></style>