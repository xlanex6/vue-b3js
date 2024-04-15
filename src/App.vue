<script setup>
import Posts from './components/Posts.vue'
import Counter from './components/Counter.vue'
import Library from './components/Library.vue'
import { ref } from "vue"


</script>

<template>

  <div class="bg-gray-100 min-h-screen p-4 m-auto max-w-md">
  
  <Posts />
  <hr>
  
  <Counter />

  <hr>
  <!-- <Library/> -->
  <Library>
    Libre text
  </Library>
  <hr>

  
</div>




</template>


