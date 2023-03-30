<script>

import { store } from '../store.js';

export default {

    name: 'AppSearch',
    data() {
        return {
            store,
        };
    },
};

</script>

<template>
    <div id="research-bar">

        <input v-model="store.searchWord" type="text" placeholder="Search a card">
        <button id="search" @click="$emit('research')"><i class="fa-solid fa-magnifying-glass"></i></button>
    </div>
</template>

<style lang="scss" scoped>
#research-bar {
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin-top: 40px;

    input {
        padding: 5px;
        border-radius: 10px;
    }

    #search {
        padding: 5px 7px;
        background-color: #242424;
        color: #f6f6f6;
        font-weight: bold;
        border: 2px solid #white;
        border-radius: 10px;
    }
}
</style>