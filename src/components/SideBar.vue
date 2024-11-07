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
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: .85rem;
    display: flex;
    align-content: flex-start;
    justify-content: flex-start;
    flex-wrap:wrap;
    gap: .8rem;
    height: 45vw;
    width: 12rem;
    box-shadow: 1px 1px 10px 0px rgb(82, 82, 82);
    border-radius: 10px;
    background-color: whitesmoke;
    padding:1rem;
    overflow:auto;
}

@media(max-width:640px){
    .notation-list{
        width: 80%;
    }
}

</style>