<script setup>
import ChessBoard from './components/ChessBoard.vue'
import SideBar from './components/SideBar.vue';
import { ref } from 'vue';

// Store data for all squares that have been clicked
const clickedSquares = ref([]);

// Receive notations via event from ChessBoard and push to clickedSquares array
function handleNotation(data) {
    clickedSquares.value.push(data);
}
</script>

<template>
  <ChessBoard @getNotation="handleNotation"></ChessBoard>
  <SideBar :notations="clickedSquares"></SideBar>
</template>
