<template>
    <div class="xm-test">xm-test
        <div class="xm-test__inner">xm-test__success</div>
        <div class="xm-test--success">xm-test__success</div>
    </div>
</template>

<script setup lang='ts' name="sassCss">
import { ref, reactive } from 'vue'

</script>
<!-- scoped  作用域 -->
<style scoped lang="scss">
@include b(test) {
    color: rgb(255, 0, 149);

    @include e(inner) {
        color: greenyellow;
    }

    @include m(success) {
        color: rgb(227, 15, 15);
    }
}
</style>