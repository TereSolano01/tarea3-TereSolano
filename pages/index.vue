<!-- pages/index.vue -->
<template>
  <div class="container">
   <HeaderView />
   <h2 style="margin-top: 15px">Canciones de Spotify más reproducidas en 2023</h2>
   <ul>
     <li v-for="song in songs" :key="song.slug">
       <NuxtLink :to="`/songs/${song.slug}`">{{song.track_name}}</NuxtLink>
     </li>
   </ul>
   <FooterView />
 </div>
</template>

<script setup>
  const data = await queryContent('songs').only('items').findOne()
  const songs = data.items
</script>

<style scoped>
@import url('../static/css/index.css');
</style>