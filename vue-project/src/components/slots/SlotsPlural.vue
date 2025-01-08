<script setup>

</script>
<template>
    <button class="fancy-btn">
        <!-- 需要區分 使用name 可以從父層指定傳入slot -->
        <slot name="icon">SlotPlural Icon</slot>
        <slot name="text">SlotPlural Text</slot> 
   </button>
   <!-- 
    <button class="default-btn">
        預設的name => default 
        <slot name="default">default</slot> 
        <slot>{{ text }}</slot>
    </button>
-->
</template>
<style>
.default-btn{
    color: black;
    background: linear-gradient(315deg, #140214 25%, #ffffff);
    border: none;
    padding: 5px 10px;
    border-radius:8px;
    cursor: pointer;
}
.fancy-btn{
    color: #fff;
    background: linear-gradient(315deg, #3caf65 25%, #5a3866);
    border: none;
    padding: 5px 10px;
    border-radius:8px;
    cursor: pointer;
    
}

</style>


