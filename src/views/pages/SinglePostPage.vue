<script setup>
import {onMounted, ref} from "vue";
import axios from "axios";

const props = defineProps({
  id: {
    type: String,
    required: true
  }
});

const SinglePost = ref([])

list();

async function list() {

  let url = `https://basic-blog.teamrabbil.com/api/post-details/${parseInt(props.id)}`
  let res = await axios.get(url);
  SinglePost.value = res.data;

}

</script>

<template>

  <!-- Post Section -->
  <section class="w-full md:w-2/3 flex flex-col items-center px-3">

    <article class="flex flex-col shadow my-4">
      <!-- Article Image -->
      <a href="#" class="hover:opacity-75">
        <img :src="SinglePost.postDetails.img">
      </a>
      <div class="bg-white flex flex-col justify-start p-6">
        <a href="#" class="text-blue-700 text-sm font-bold uppercase pb-4">{{ SinglePost.postDetails.title }}</a>

        <p class="pb-3">{{ SinglePost.postDetails.content }}</p>

      </div>
    </article>
  </section>
</template>

<style scoped>

</style>