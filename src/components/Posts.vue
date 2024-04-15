<template>
  <div>

    <input type="number" :max="maxPosts" min="0" v-model="postCounter">

    <!-- <button class="bg-red-500 rounded-xl px-4 py-1 font-bold shadow-lg text-white mx-2"> Get {{ postCounter }} Posts
    </button> -->


    <Btn @click="fetchPosts" :disabled="postCounter > maxPosts + 1" variant="success">
      Get {{ postCounter }} Posts 
    </Btn>



    <article v-for="post in posts" :key="post.id" class="mb-8">
      <h3 class="text-xl font-bold">{{ post.title }}</h3>
      <p class="text-sm mb-2">{{ post.body }}</p>
      <hr>
    </article>

  </div>
</template>

<script setup>
import { ref } from "vue";
import Btn from "./Button.vue";
const postCounter = ref(5)
const maxPosts = 5
const posts = ref([])

async function fetchPosts() {
  const res = await fetch(`https://dummyjson.com/posts?limit=${postCounter.value}`)
  const { posts: postData, skip, limit } = await res.json()
  posts.value = postData
}

</script>
<style scoped>
.winner {
  color: green;
}

.looser {
  color: red;
}
</style>
