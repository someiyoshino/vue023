<script setup>
import TheHeader from './components/TheHeader.vue';
import TheFooter from './components/TheFooter.vue';
</script>

<template>
    <div class="wrap">
        <TheHeader />
        <main class="main">Main</main>
        <TheFooter />
    </div>
</template>

<style>
@import 'assets/css/destyle.css';

.wrap {
    background-color: rgba(207, 221, 233, 0.3);
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    width: 370px;
    margin: 0 auto;
    font-family: sans-serif;
}
.main {
    background-color: rgba(207, 233, 223, 0.3);

    flex: 1;
    width: 100%;
}
</style>
