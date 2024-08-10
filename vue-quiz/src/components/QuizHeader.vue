<script setup>
import { defineProps } from 'vue';

const { questionPage, barPercentage } = defineProps(["questionPage", "barPercentage"])
</script>

<template>
    <div>
        <header>
            <h3>Questions {{ questionPage }}</h3>
            <div class="bar">
                <div class="bar-progress" :style="{width: barPercentage}"></div>
            </div>
        </header>
    </div>
</template>

<style scoped>
header {
    margin-top: 20px;
}
header h3 {
    font-size: 20px;
}

.bar {
    width: 100%;
    height: 50px;
    border: 3px solid #adf7b6;
}
.bar-progress {
    height: 100%;
    width: 0%;
    background-color: #adf7bd;
}
</style>