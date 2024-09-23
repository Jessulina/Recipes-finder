<script setup>

</script>
<template>
    <div class="d-flex justify-content-between">
        <button id="show-more-btn" class="btn btn-secondary btn-lg m-4">Show more <i class="bi bi-arrow-down"></i></button>
        <a id="back-to-top-btn" class="btn btn-secondary btn-lg m-4" href="#top">Back to top <i class="bi bi-arrow-up"></i></a>
        <!--WHY WHEN I RENDER THE PAGE THE PATH IS STILL /#top? -->
    </div>
</template>

<style coped>

.show-more-btn {
    margin-top: 20px;
    background-color: #ff5722;
    color: #fff;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
}

.show-more-btn:hover {
    background-color: #e64a19; 
}

</style>