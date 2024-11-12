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
    list-style-position: inside;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: .8rem;
    color: #ffffff;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    align-content:baseline;
    justify-items: center;
    height: 80%;
    width: 18rem;
    border-radius: 10px;
    background-color: #252525;
    padding: 1rem;
    overflow: auto;
    margin: 1rem 0rem 0rem 0rem;
    gap: .6rem;
}

li {
    text-align: center;
    width: 85%;
    padding: .2rem;
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