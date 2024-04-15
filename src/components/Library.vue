<template>
  <!-- <Btn @click.once="addVanilla()"> Add vanilla </Btn> -->
  <input type="text" v-model="userInput" class=" rounded-md text-gray-400 px-1 focus:inset-red-500">

  <Btn @click="addUserInput"> Add </Btn>
  <ul>
    <li v-for="lib in libs" :key="lib"> {{ lib }}</li>
  </ul>
  <p class="text-red-500 uppercase font-bold italic">
    <slot />
  </p>
</template>

<script setup>
import { ref } from "vue"
const userInput = ref('')
import Btn from "./Button.vue";

const libs = ref(['vue', 'react', 'angular', 'svelte', 'astro']) 
function addUserInput() {
  libs.value.push(userInput.value)
  userInput.value = ''
}

</script>
