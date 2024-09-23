<script setup>
    import PaginationButtons from './PaginationButtons.vue';

    const props = defineProps({
        recipes: {
            type: Array,
            required: true
        }
    })

</script>

<template>
    <section class="container" v-if="recipes.length">
        <div class="row">
            <div v-for="recipe in recipes" 
                :key="recipe.uri" 
                class="col-lg-3 col-mb-4 col-sm-4">
                <div class="card mb-4">
                    <a 
                        :href="recipe.url" 
                        target="_blank" 
                    > 
                        <img 
                            :src="recipe.image" 
                            :alt="recipe.label" 
                            class="card-img-top">
                        <div class="card-body d-flex-row">
                            <h5 class="card-title mt-1">
                                {{ recipe.label }}
                            </h5>
                        </div>
                    </a>
                </div>
            </div>
        </div>
        <PaginationButtons />
        </section>
</template>

<style scoped>
.container {
    position: relative;
    width: 100%;
    height: 70vh;
}
a {
    text-decoration: none;
}
.card {
    transition: box-shadow 0.3s ease-in-out; /* Transición suave para el hover */
}
/*.card-img-top {
    object-fit: cover;
}*/
.card:hover {
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.9), 0 6px 20px rgba(0, 0, 0, 0.6);
}
/*FALTA QUE SE MUESTRE TODA LA IMAGEN BIEN ENCAJADA DENTRO DE LA CARD*/ 
.card-title {
    color: var(--vt-c-black);
    font-weight: 500;
    height: 3em;
    text-align: center;
}
.card-title:hover {
    font-weight: 800;
}

</style>
