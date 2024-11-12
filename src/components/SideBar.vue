<script setup>
    // Receive clickedSquares array as a prop
    const props = defineProps({
        notations: Array
    })

</script>

<template>
    <ol class="notation-list">
        <li v-for="notation in notations">
        {{ notation.square }}
        </li>
    </ol>
</template>

<style scoped>
.notation-list{
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: .85rem;
    color: #ffffff;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-content: flex-start;
    justify-content: center;
    gap: .6rem;
    height: 80%;
    width: 18rem;
    border-radius: 10px;
    background-color: #252525;
    padding: 1rem;
    overflow: auto;
    margin-top: 1rem;
}

li {
    text-align: center;
    width: 10%;
    padding: .2rem 1rem;
    margin: .5rem;
    height: min-content;
    background-color: #383838;
    border-radius: 3px;
}

@media(max-width:640px){
    .notation-list{
        max-height: 20%;
        width: 80vw;
        margin-top: 0;
    }
}

</style>