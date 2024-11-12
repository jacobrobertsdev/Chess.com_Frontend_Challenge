<script setup>
import { ref } from 'vue'

const emit = defineEmits(['getNotation']);
const squares = ref([]);
const highlightedSquare = ref(null);
// let count = 0;

// Initialize the chess board
function createBoard() {
  // Row and Column values
  const rows = [8, 7, 6, 5, 4, 3, 2, 1];
  const columns = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'];

  // // Create 64 squares calculating row and column. Set algebraic notation and color properties for each square object.
  // for (let i = 0; i < 64; i++){

  //   let row = Math.floor(i / 8);
  //   let col = i % 8;

  //   squares.value.push({
  //     // highlighted: false,
  //     notation: columns[col] + `${rows[row]}`,
  //     light: (col + row) % 2 === 0 // Determine if dark/light square with boolean
  //   })
  // }


  // Use flatMap to create 64 squares with row and column combinations
  squares.value = rows.flatMap((row, rowIndex) => 
    columns.map((col, colIndex) => ({
      notation: `${col}${row}`,
      light: (colIndex + rowIndex) % 2 === 0 // Determine if dark/light square with boolean
    }))
  );
}
createBoard();

// Handle each square click
function handleClick(square) {
  // Remove highlight from all squares
  // squares.value.forEach(s => s.highlighted = false);

  highlightedSquare.value = square;

  // // Update square.highlighted for current square using square value
  // square.highlighted = true;

  // Increment count
  // count += 1;

  // Emit count and notation data to use in SideBar component
  emit('getNotation', {
    // count: count,
    square: square.notation
  });
}
</script>

<template>
<div class="board">
  <div v-for="square in squares"
   :key="square.index" 
   :class="['square', { isHighlighted:square === highlightedSquare, lightSquare:square.light }]"
   @click="handleClick(square)"
   >
  </div>
</div>
</template>

<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  grid-template-rows: repeat(8, 1fr);
  max-width: 50vw;
  height: 50vw;
  max-height: 95vh;
  aspect-ratio: 1;
  margin: 1rem;
}

.square {
  background-color: #739552;
}

.lightSquare{
  background-color: #ebecd0;
}

.isHighlighted{
  background-color: rgb(56, 213, 252);
}

</style>
