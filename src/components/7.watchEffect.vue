<template>
    <div>
        <input id="Inputdom" type="text" v-model="data1"><br>
        <input type="text" v-model="data2"><br>
        <button @click="stop">停止监听</button>
    </div>
</template>

<script setup lang='ts' name="watchEffectData">
import { ref, reactive, watchEffect } from 'vue'
let data1 = ref<string>("非惰性监听函数");
let data2 = ref<string>("什么叫非惰性监听函数");
const startWatch = watchEffect((onInvalidate) => {
    let Inputdom: HTMLInputElement = document.querySelector("#Inputdom") as HTMLInputElement;
    console.log(Inputdom);//获取监听到的元素
    //非惰性监听  进页面就会调用
    console.log(data1.value);
    console.log(data2.value);//监听多个就再写一行
    onInvalidate(() => {
        //监听之前做的回调
        console.log("监听之前做的回调")
    })
}, {
    flush: 'pre',//加载完整后
    onTrigger(e) {
        debugger //触发回调
    }
})
const stop = () => startWatch();//停止监听
</script>
<style scoped></style>