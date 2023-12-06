<script setup>
import SearchInput from './components/Searchinput.vue';
</script>

<template>
  <main>
    <div class="text-center mb-6">
      {{ new Date().toLocaleDateString('en-us', {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      }) }}
    </div>
    <div>
      <SearchInput/>
    </div>
  </main>
</template>