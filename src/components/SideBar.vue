<script setup>

// Receive clickedSquares array as a prop
    const props = defineProps({
        notations: Array
    })

</script>


<template>
   
    <ul class="notation-list">
    <li v-for="notation in notations">
    {{ `${notation.count}. ` + notation.square }}
    </li>
    </ul>
</template>

<style scoped>
.notation-list{
    list-style-type: none;
    display: flex;
    flex-direction: column;
    align-content: center;
    justify-content: flex-start;
    flex-wrap: wrap;
    gap: 1rem;
    width: 27rem;
    height: 16rem;
    box-shadow: 1px 1px 10px 0px rgb(82, 82, 82);
    border-radius: 10px;
    background-color: white;
    padding: 2rem;

}


</style>