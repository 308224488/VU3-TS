<template>
    <!-- <div>
        <header class="header">头部</header>
        <main class="main">
            匿名插槽
            <slot>

            </slot>
        </main>
        <footer class="footer">尾部</footer>
    </div> -->
    <!-- ——————————————————匿名插槽在父组件的用法————————————————————————
    <template>
        <chaCaoData>
            <template v-slot>
                <div>
                    匿名插槽 从父组件向子组件插入内容
                </div>
            </template>
        </chaCaoData>
    </template>
    ——————————————————匿名插槽在父组件的用法———————————————————————— -->

    <div>
        <header class="header">头部
            <slot name="header"></slot>
        </header>
        <main class="main">
            <!-- 具名插槽 -->



        </main>
        <footer class="footer">
            <div v-for="(item, index) in data" :key="index">
                <slot :index="index" name="footer" :data="item"></slot>
            </div>
            尾部
        </footer>
    </div>
</template>
<script setup lang='ts' name="chaCaoData">
import { ref, reactive } from 'vue'
type name = {
    name: string,
    number: number
}
const data = reactive<name[]>([
    {
        name: "插槽作用域1",
        number: 1
    },
    {
        name: "插槽作用域2",
        number: 2
    },
    {
        name: "插槽作用域3",
        number: 3
    }
])
</script>
<style scoped>
.header {

    height: 300px;
    width: 300px;
    background-color: aquamarine;
    border: 1px solid aquamarine;
}

.main {
    height: 300px;
    width: 300px;
    background-color: rgb(164, 15, 20);
    border: 1px solid rgb(164, 15, 20);
}

.footer {
    height: 300px;
    width: 300px;
    background-color: rgb(236, 240, 9);
    border: 1px solid rgb(236, 240, 9);
}
</style>