<template>
    <div>
        <form>
            <input type="text" v-model="from.name" />
        </form><br>
        <!-- @click.prevent 阻止默认提交事件 -->
        <button @click.prevent="submit">demo1</button>
    </div>
    <!-- recative demo2 数组 -->
    <ul>
        <li v-for="item in arrayData">{{ item }}</li>
    </ul>
    <button @click="add">recative 数组</button>
    <!-- 方式一 -->
    <ul>
        <li v-for="item in arrayData">{{ item }}</li>
    </ul>
    <button @click="add2">recative 数组方式一</button>
    <!-- 方式二 -->
    <ul>
        <li v-for="item in arrayData2.arr">{{ item }}</li>
    </ul>
    <button @click="add3">recative 数组方式二</button>
</template>

<script setup lang='ts' name="recativeData">
import { ref, reactive } from 'vue'
// ref和reactive的区别
// ref支持所有类型   reactive只支持引用类型 数组 object map set
// ref取值赋值都需要加.value reactive取值赋值不需要加.value
let from = reactive({
    name: 'demo',
})
const submit = () => {
    console.log(from);
}

const arrayData = reactive<number[]>([]);
const arrayData2 = reactive<{ arr:number[]}>({arr:[]});
const add = () => {
    arrayData.push(1);
}
// recative proxy不能直接赋值 否则会破坏响应式对象  解决方案 数组 可以使用push加解构
const add2 = () => {
    let res = [1, 2, 3, 4];
    arrayData.push(...res);//解构
    console.log(arrayData);
}
const add3 = () => {
    let res = [1, 2, 3, 4];
    arrayData2.arr=res;
}
</script>
<style scoped></style>