<template>
    <div ref="div">
        {{ data }}
    </div>
    <button @click="change"> 生命周期的按钮</button>
</template>

<script setup lang='ts' name="shengMingZhouQi">
import { ref, reactive, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted, onRenderTracked, onRenderTriggered } from 'vue'
console.log('setup');
const data = ref('生命周期');
const div = ref<HTMLDivElement>();
const change = () => {
    data.value = '生命周期组件更新';
}
//创建完整的生命周期
onBeforeMount(() => {
    console.log('onBeforeMount 创建之前', div.value)
})
onMounted(() => {
    console.log('onMounted 创建完成', div.value)
})
onBeforeUpdate(() => {
    console.log('onBeforeUpdate 更新组件之前')
})
onUpdated(() => {
    console.log('onUpdated 更新组件完成')
})
onBeforeUnmount(() => {
    console.log('onBeforeUnmount 销毁之前')
})
onUnmounted(() => {
    console.log('onUnmounted 销毁完成')
})
//销毁是在父组件销毁的时候执行

//调试时用的
onRenderTracked((e) => {
    console.log('onRenderTracked 更新之前调试时用的', e)
})
onRenderTriggered((e) => {
    console.log('onRenderTriggered 更新之后调试时用的', e)
})
</script>
<style scoped></style>