<template>
    <div style="display: flex;">
        <div @click="changTab(item, index)" :class="[active == index ? 'active' : '']" class="tableStyle"
            v-for="(item, index) in data" :key="index">
            <div>{{ item.name }}</div>
        </div>
    </div>
    <component :is="comId"></component>
</template>

<script setup lang='ts' name="dongTaiZuJianData">
// 动态组件
import { ref, reactive, markRaw } from 'vue';
import ChuanCanData from './10.ChuanCan.vue';
import sassCss from './9.sass.vue';
import shengMingZhouQi from './8.shengmingzhouqi.vue';
const comId = ref(ChuanCanData)
const active = ref(0);
const data = reactive([
    {
        name: '组件1 ChuanCanData ',
        com: markRaw(ChuanCanData)
    },
    {
        name: '组件2 sassCss ',
        com: markRaw(sassCss)
    },
    {
        name: '组件3 shengMingZhouQi ',
        com: markRaw(shengMingZhouQi)
    }

])
const changTab = (item: any, index: number) => {
    comId.value = item.com;
    active.value = index;
}
</script>
<style scoped lang="less">
.active {
    background-color: aquamarine;
    cursor: pointer;
}

.tableStyle {
    border: 1px solid #1dac57;
    margin: 3px;
    padding: 3px;
    cursor: pointer;
}
</style>