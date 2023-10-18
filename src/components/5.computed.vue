<template>

<div>
    姓:<input type="text" v-model="firstName"/>
</div>
<div>
    名:<input type="text" v-model="lastName"/>
</div>
<div>
    全名:{{ name }}
    函数式写法:{{ name2}}
</div>
<button @click="change">set更改</button>
</template>

<script setup lang='ts' name="computedData">
import { ref,computed} from 'vue'
let firstName = ref('小');
let lastName = ref('刘');
// 选项式写法 支持一个对象传入get函数以及set函数自定义操作
let name=computed({
    get(){
        return firstName.value + lastName.value;
    }, 
    set(Nvalue){
       [firstName.value,lastName.value]=Nvalue.split('死');
    }
})
const change=()=>{
    name.value='打死以色列！' 
}
// 函数式写法 只能支持一个getter 函数不允许修改值的
let name2=computed(()=>{
   return firstName.value+lastName.value;
})
</script>
<style scoped>

</style>