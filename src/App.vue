<script setup>
import axios from 'axios'
import { ref } from 'vue'

import ResultsSection from './components/ResultsSection.vue'

const appId = '11dc9b37'; 
const appKey = '62102ba475f9da330521bb14ff1d40d9'; 
const query = ref('')
const recipes = ref([])
const errorMessage = ref('')

const getData = async () => {
  
  if (!query.value.trim()) {
    errorMessage.value = 'Please enter a word, such as "chicken", "Italian", or "chocolate cake".';
    return;
  }

  const ingredients = query.value.split(',').map(ingredient => ingredient.trim()).join(',');

  try {
    const { data } = await axios.get('https://api.edamam.com/search', {
      params: {
        q: ingredients,
        app_id: appId,
        app_key: appKey,
        from: 0,
        to: 8 // will be modified when i implement the pagination/scroll button
      }
      
    });
    
    if (data.hits.length === 0) {
      errorMessage.value = 'No recipes found. Please try a different keyword.';
    } else {
      errorMessage.value = '';
      recipes.value = data.hits.map(hit => hit.recipe) || [];
    }

    query.value = '';
    
  } catch (error) {
    console.log(error);
    errorMessage.value = 'An error occurred while fetching data. Please try again.';
  }
};

</script>

<template>
  <main>
    <img 
      :class="{ hidden: recipes.length > 0 }" 
      class="img-fluid background" 
      alt="Food background" 
      src="./assets/food.jpg" 
    />
      <section
        id="top"
        :class="{ centered: recipes.length > 0  }"
        class="search-section d-flex align-items-center flex-column"
      >
        <h1 class="display-1"><strong>Feeling hungry?</strong></h1>
        <h2 class="h2 mb-4"> Let’s see what recipes we can find!</h2>
        <form @submit.prevent="getData" role="search" class="mb-4">
          <input 
            v-model="query" 
            class="form-control me-1"
            type="search" 
            placeholder="Search for recipes by ingredient, cuisine type, name..."
            aria-label="Search for recipes by ingredient, cuisine type, or recipe name. 
                        For example: chicken, Italian, chocolate cake"
            autocomplete="off"            
          /> 
          <button 
            @click="getData" 
            id="button" 
            class="btn btn-lg"
            type="submit" 
            aria-label="Submit search"
          > Search
          </button>
        </form>
        <p v-if="errorMessage" class="text-danger  fs-6">{{ errorMessage }}</p>
    </section>
    <ResultsSection :recipes="recipes" />

  </main>
  
</template>

//TO DO
//scroll button to shw more results
//check responsive design


