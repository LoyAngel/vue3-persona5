<template>
    <view class="view-main">
        <view
            class="view-item"
            v-for="(tab, index) in tabBars"
            :key="tab.id"
            :class="navIndex === index ? 'active' : ''"
            @click="$emit('checkIndex', index)"
        >
            {{ tab.name }}
        </view>
    </view>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';
interface TabBarItem {
    name: string;
    id: string;
    image: string;
    details: string;
}
const props = defineProps<{
    navIndex: number;
    tabBars: TabBarItem[];
}>();
</script>

<style scoped>
.active {
    color: #ff0000;
    border-bottom: 2px solid #ff0000;
    transition: color 0.3s, border-bottom 0.3s;
}

.view-main {
    white-space: nowrap;
    color: #CCCCCC;
    background-color: #000000;
    width: 100vw;

    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: space-around;
    align-items: center;
}

.view-item {
    flex: 1 0 auto;
    padding: 10px;
    text-align: center;
    transition: color 0.3s;
}

.view-item:hover {
    color: #ff0000;
}
</style>