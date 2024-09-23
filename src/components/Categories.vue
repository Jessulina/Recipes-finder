<script setup>

</script>

<template>
    <div class="foods">
        <h1>What is your favorite?</h1>
        <ul>
            <li v-for="food in foods">
                
            </li>
        </ul>
    </div>
</template>

<style scoped>
    .foods {
        width: 100vw;
        height: 20%;
        border: 1px solid black;
        z-index: 2;
        display: flex;
        justify-content: center;
        align-items: flex-start;
    }
</style>