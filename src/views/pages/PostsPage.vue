<script setup>
import SideBarComponent from "@/components/SideBarComponent.vue";

// const props = defineProps({
//   id: {
//     type: String,
//     required: true
//   }
// });


import axios from "axios";
import {ref} from "vue";

const postList = ref([])


list();

async function list() {

  let url = "https://basic-blog.teamrabbil.com/api/post-newest"
  let res = await axios.get(url);
  postList.value = res.data;
}

</script>

<template>
  <div class="container mx-auto flex flex-wrap py-6">

    <!-- Posts Section -->
    <section class="w-full md:w-2/3 flex flex-col items-center px-3">

      <article v-for="post in postList" :key="post.id" class="flex flex-col shadow my-4">
        <!-- Article Image -->
        <a href="#" class="hover:opacity-75">
          <img :src="post.img">
        </a>
        <div class="bg-white flex flex-col justify-start p-6">
          <RouterLink :to="{name:'SinglePostPage',params:{id:post.id}}"
                      class="text-blue-700 text-sm font-bold uppercase pb-4">{{ post.title }}
          </RouterLink>
          <RouterLink :to="{name:'SinglePostPage',params:{id:post.id}}"
                      class="text-3xl font-bold hover:text-gray-700 pb-4">{{ post.short }}
          </RouterLink>
        </div>
      </article>


    </section>
    <SideBarComponent/>
  </div>

</template>

<style scoped>

</style>