<script setup>

const text = "123"


</script>
<template>
    <button class="fancy-btn">
        <slot>Default</slot> <!-- slot 出口 -->
        <!-- 防止無傳入資料 可預設內容 -->
        {{ text }}
   </button>
</template>
<style>
.fancy-btn{
    color: #fff;
    background: linear-gradient(315deg, #42d392 25%, #647eff);
    border: none;
    padding: 5px 10px;
    border-radius:8px;
    cursor: pointer;
    
}

</style>


