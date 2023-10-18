<template>
    <div>子组件接收父组件传来的值:{{ title }}</div>
    <div>使用ts的方式定义 子组件接收父组件传来的值:{{ title }}</div>

    <button @click="send">给父组件传值</button>
</template>

<script setup lang='ts' name="ChuanCanData">
import { ref, reactive, defineProps, withDefaults, defineEmits, defineExpose } from 'vue'
//接收父组件传过来的值
// defineProps({
//     title: {
//         type: String,//String Number Boolean Array Object Function Date Symbol
//         default: '子组件接收父组件传来的值'
//     }
// })
//方式二
// const props= defineProps({
//     title: {
//         type: String,//String Number Boolean Array Object Function Date Symbol
//         default: '子组件接收父组件传来的值'
//     }
// })
//alert(props.title)
// 方式三 使用ts的方式定义
// const props = defineProps<{
//     title: string,
// }>();
//设置接收的默认值
const props2 = withDefaults(defineProps<{
    title: string,
}>(), {
    title: '子组件接收父组件传来的默认值'
})


//给父组件传值
const emit = defineEmits(['click']);
const send = () => {
    emit('click', "子组件给父组件传值")
}
//将值或者方法暴露给父组件
const requestData = () => {
    console.log("将方法暴露给父组件");
}
defineExpose({
    name:()=> "将属性值暴露给父组件",
    // requestData
});
</script>
<style scoped></style>