

<template>
  <!-- 插值表达式 -->
  <span>{{ data }}</span><br>
  <!-- 插值表达式运算符 -->
  <span>{{ data2 + 1 }}</span><br>
  <!-- 插值表达式三元运算符 -->
  <span>{{ data3 ? 'yes' : 'no' }}</span><br>
  <!-- 插值表达式API运算符 -->
  <span>{{ data4.map(item => ({ num: item })) }}</span><br>
  <!-- vue指令v-text -->
  <span v-text="data5"></span>
  <!-- vue指令v-html 可以解析html标签 -->
  <span v-html="data6"></span><br>
  <!-- vue指令v-if -->
  <span v-if="data7 == 3">v-if!</span>
  <!-- vue指令v-else-if -->
  <span v-else-if="data7 == 2">v-else-if</span>
  <!-- vue指令v-else v-else 是用于与 v-if 或 v-else-if 结合使用的指令-->
  <span v-else>v-else!</span><br>
  <!-- vue指令v-show 效率更高-->
  <span v-show="data7 == 1">v-show!</span><br>
  <!-- vue指令 v-on:click 点击事件 用@代替 -->
  <button @click="action">click</button><br>
  <!-- vue指令 v-on:click 点击事件 支持动态事件切换-->
  <button @[data8]="action">动态事件click</button><br>
  <!-- vue指令 v-on:click 点击事件 属性选择-->
  <button @[data8].once="action">动态事件属性</button><br>
  <!-- vue指令v-bind 绑定元素上的属性 用:代替 id style name -->
  <button :id="data8">v-bind</button><br>
  <!-- vue指令v-bind 绑定元素上的属性 支持表达式 -->
  <button :class="[data9 ? 'true' : 'false']">v-bind表达式</button><br>
  <!-- vue指令v-model  -->
  <input type="text" v-model="data10"><br>
  <span>{{ data10 }}</span><br>
  <!-- vue指令 v-for -->
  <span v-for="(item, index) in data11" :key="index">{{ index }}--{{ item }}</span><br>
  <!-- vue指令 v-once 只会渲染一次 -->
  <span v-once>只会渲染一次</span><br>
</template>
<script setup lang="ts" name="VUE_ZhiLing">
import { ref } from 'vue';//响应式数据
const data: number = 1;
const data2: number = 2;
const data3: number = 3;
const data4: number[] = [1, 2, 3, 4];
const data5: string = 'hello world';
const data6: string = '<h3 style="color:blue">hello world</h3>';
const data7: number = 1;
const data8: string = 'click';
const data9: boolean = true;
const data10 = ref('v-model');
const data11: string[] = ['a', 'b', 'c'];

const action = () => {
  alert("hello world");
}
</script>
<style scoped>
.true {
  color: green;
}

.false {
  color: rgba(219, 42, 172, 0.549);
}

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
