<template>
  <p v-if="count >= 10" class="winner">GAGNÉ</p>
  <p v-else class="looser">PERDU</p>

  <Btn @click="decrementCount()"> - </Btn>
  Nombre de clicks: {{ count }}
  <Btn @click="incrementCount()"> + </Btn>
</template>

<script setup>
import { ref } from "vue"
import Btn from "./Button.vue";

const count = ref(0)
function incrementCount() {
  // count.value = count.value + 1
  count.value++
}
function decrementCount() {
  // count.value = count.value + 1
  if (count.value > 0) {
    count.value--
  }
}
</script>
