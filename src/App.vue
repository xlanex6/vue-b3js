<script setup>
import { ref } from "vue"

// const count = ref(0)
// const userInput = ref('')



// const libs = ref(['vue','react','angular','svelte','astro']) 

// function incrementCount() {
//   // count.value = count.value + 1
//   count.value ++
// }
// function decrementCount() {
//   // count.value = count.value + 1
//   if (count.value > 0) {
//     count.value--
//   }
// }

// function addVanilla() {
//   libs.value.push('vanilla')
// }
// function addUserInput() {
//   libs.value.push(userInput.value)
//   userInput.value = ''
// }

const postCounter = ref(0)
const maxPosts = 5
const posts = ref([])

async function fetchPosts() {
  const res = await fetch(`https://dummyjson.com/posts?limit=${postCounter.value}`)
  const { posts: postData, skip , limit } = await res.json()
  posts.value = postData
}

</script>

<template>

  <!-- <p v-if="count >= 10" class="winner">GAGNÉ</p>
    <p v-else class="looser">PERDU</p>
    
    <button @click="decrementCount()"> - </button>
    Nombre de clicks: {{ count }}
    <button @click="incrementCount()"> + </button>
    
    <hr> -->

  <!-- <button @click.once="addVanilla()"> Add vanilla </button> -->
  <!-- <input type="text" v-model="userInput">
  <button @click="addUserInput"> Add </button>
  <ul>
    <li v-for="lib in libs" :key="lib"> {{ lib }}</li>
  </ul> -->

  <input type="number" :max="maxPosts" min="0" v-model="postCounter">

  <button @click="fetchPosts" v-bind:disabled="postCounter > maxPosts + 1"> Get {{ postCounter }} Posts </button>

  <article v-for="post in posts" :key="post.id">
    <h3>{{ post.title }}</h3>
    <p>{{ post.body }}</p>
  </article>

</template>

<style scoped>
.winner {
  color: green;
}

.looser {
  color: red;
}
</style>
