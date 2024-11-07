<script setup>
import { ref } from 'vue'

const emit = defineEmits(['getNotation']);
const squares = ref([]);
let count = 0;

// Initialize the chess board
function populateBoard() {
  // Row and Column values
  const rows = [8, 7, 6, 5, 4, 3, 2, 1];
  const columns = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'];

  // Create 64 squares calculating row / column. Set algebraic notation and color properties for each square object.
  for (let i = 0; i < 64; i++){

    let row = Math.floor(i / 8);
    let col = i % 8;

    squares.value.push({
      index: i,
      highlighted: false,
      notation: columns[col] + `${rows[row]}`,
      dark: (col + row) % 2 === 0 // Determine if dark/light square with boolean
    })
  }
}

populateBoard();


// Handle each square click
function handleClick(index) {
  // Remove highlight from all squares
  squares.value.forEach(square => square.highlighted = false);

  // Update square.highlighted for current square using index value
  squares.value[index].highlighted = true;

  // Increment count
  count += 1;

  // Emit count and notation data to use in SideBar component
  emit('getNotation', {
    count: count,
    square: squares.value[index].notation
  });
}

</script>

<template>
<div class="board">
  <div v-for="square in squares"
   :key="square.index" 
   :class="['square', { isHighlighted:square.highlighted, darkSquare:square.dark }]"
   @click="handleClick(square.index)"
   >
</div>
</div>
</template>

<style scoped>
.board {
  box-shadow: 1px 1px 10px 0px rgb(82, 82, 82);
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  grid-template-rows: repeat(8, 1fr);
  width: 35rem;
  height: 35rem;
  gap: 0;
}

.square {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  height: 100%;
  background-color: beige;

}

.darkSquare{
  background-color: rgb(114, 168, 70);
}

.isHighlighted{
  background-color: rgb(56, 213, 252);
}

@media (max-width: 720px) {
  .board {
    width: 28rem;
    height: 28rem;
  }
}

@media (max-width: 455px) {
  .board {
    width: 23rem;
    height: 23rem;
  }
}
</style>
