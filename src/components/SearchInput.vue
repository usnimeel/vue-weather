<script setup>
import { ref } from 'vue';

const searchTerm= ref('')
const results = ref(null)
const handleSearch = async () => {
    if (searchTerm.value !== '') {
        const res = await fetch(`http://api.weatherapi.com/v1/search.json?key=${import.meta.env.VITE_WEATHER_API}&q=${searchTerm.value}`)
        const data = await res.json()
        results.value = data
    }
}
</script>

<template>
    <div>
        <!-- Search Field -->
        <form>
            <div class="bg-white my-2 rounded-lg shadow-lg flex item-center border">
                <i class="fa-solid fa-magnifying-glass p-2"></i>
                <input 
                    type="text"
                    placeholder="e.g Halifax"
                    class="w-full"
                    v-model="searchTerm"
                   @input="handleSearch"
                />
            </div>
        </form>
        <!-- Search suggestions -->
        <div class="bg-white my-2 rounded-lg shadow-lg">
            <div v-if="results !== null">
                <div v-for="place in results" :key="place.id">
                    <button class="px-3 my-2">
                        {{ place.name }}, {{ place.region }}, {{ place.country }}
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>