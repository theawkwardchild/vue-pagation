<script setup lang="ts">
import Pagation from './components/Pagation.vue'

import { ref } from "vue";
var displayPage = ref(1);
var lastPage = ref(12);

function pageUpdate(newPage: number) {
  // add any logic needed to display the next page here
  displayPage.value = newPage
}
</script>

<template>
  <main>    
    <Pagation v-on:updatePager="pageUpdate($event)" :current="displayPage" :last="lastPage" />
            <h1>{{displayPage}} / {{lastPage}}</h1>
            <input type="number" min="1" :value="lastPage" @input="event => {lastPage = parseInt(event.target.value); if(lastPage < displayPage) displayPage = lastPage}" />
  </main>
</template>

<style scoped>


</style>
