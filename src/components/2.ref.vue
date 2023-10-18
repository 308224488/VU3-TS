<template>
    <!-- ref深层响应式数据  demo1 -->
    <div>
        {{ data1 }}
        <button @click="change">demo1</button>
    </div>
    <!-- ref响应式数据  demo2 -->
    <div>
        判断是否是ref对象
        <button @click="change2">demo2</button>
    </div>
    <!-- shallowRef浅层响应式数据  demo3 -->
    <div>
        <!-- ref和shallowRef不能一起去用，否则会一起造成视图的更新    -->
        <button @click="change3">浅层响应式数据 只改变.value的值</button>
        {{ data1 }}
        <button @click="change4">浅层响应式数据 这样就是响应式了</button>
    </div>
</template>

<script setup lang='ts' name="refData">
import { ref, isRef, shallowRef } from 'vue'
const data1 = ref<Data>({ name: 'demo1', age: 18 });
type Data = {
    name: string;
    age: number;
}
const change = () => {
    data1.value.name = '改变demo1的值';
    data1.value.age = 20;
}
// 判断是否是ref对象
const change2 = () => {
    alert(isRef(data1))
}
const change3 = () => {
    data1.value.name = '只改变.value的值';
    console.log(shallowRef(data1.value.name));
}
const change4 = () => {
    data1.value = {
        name: "这样就是响应式了",
        age: 22
    }
    console.log(shallowRef(data1.value.name));
}
</script>
<style scoped></style>