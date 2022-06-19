<template>
    <div class="thermometer-bg">
        <div class="thermometer">
            <div class="thermometer-body">
                <div ref="thermometerFillRef" class="thermometer-body-fill"></div>
            </div>
            <div class="thermometer-bottom">
                <div class="thermometer-bottom-fill"></div>
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">
import { ref, onMounted } from 'vue'

const thermometerFillRef = ref<HTMLDivElement | null>()

onMounted(() => {
    setTimeout(() => {
        thermometerFillRef.value.style.setProperty("top", "20px")
    }, 9000);
})

</script>
<style scoped>

.thermometer {
    width: 200px;
    margin: 0 auto;
    position: relative;
}

.thermometer-bottom,
.thermometer-body {
    background-color: #ededfa;
    border: 15px solid #d8d9e8;
    margin: 0 auto;
}
.thermometer-bottom,
.thermometer-bottom-fill {
    margin: 0 auto;
    border-radius: 50%;
    z-index: 0;
}
.thermometer-bottom {
    height: 120px;
    width: 120px;
}

.thermometer-bottom::before {
    content: "";
    background-color: #db1d1d;
    height: 15px;
    width: 40px;
    position: absolute;
    left: 80px;
    z-index: 1;
}

.thermometer-bottom-fill {
    background-color: #db1d1d;
    height: 98px;
    width: 98px;
    position: relative;
    top: 11px;
    transition: top 0.5s cubic-bezier(0.33, 1, 0.68, 1);
}

.thermometer-body,
.thermometer-body-fill {
    margin: 0 auto;
    border-radius: 50px 50px 0 0;
    z-index: 1;
}

.thermometer-body {
    height: 325px;
    width: 60px;
    border-bottom: 0;
    position: relative;
    bottom: -23px;
    overflow: hidden;
}

.thermometer-body-fill {
    background-color: #db1d1d;
    height: 320px;
    width: 40px;
    position: relative;
    top: 160px;
    transition: top 0.5s linear;
}

</style>
