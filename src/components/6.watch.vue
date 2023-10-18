<template>
    <div>
        <input type="text" v-model="message"><br>
        <input type="text" v-model="message2"><br>
        <input type="text" v-model="message3.info.name"><br>
    </div>
</template>

<script setup lang='ts' name="watchData">
import { ref, reactive, watch } from 'vue'
let message = ref<string>('监听单个数据');
let message2 = ref<string>('监听多个数据');
let message3 = ref({
    info: {
        name: '张三',
        age: 18,
        sex: '男'
    }
})
// watch([message,message2], (newValue, value) => {
//     console.log(newValue, value);
// })
watch(message3, (newValue, oldValue) => {
    console.log(newValue, oldValue); //如果是引用类型，新值和旧值是同一个
}, {
    deep: true,// 深度监听 监听ref嵌套对象的值的变化
    immediate: true, //立即执行
    flush: 'pre'// 组件更新之前调用   sync 同步执行 post组件更新之后执行
})
</script>
<style scoped></style>