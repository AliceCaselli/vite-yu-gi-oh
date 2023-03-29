<script>

import { store } from "../store.js";
import axios from "axios";
import CardsItem from "./CardsItem.vue";

export default {
    data() {
        return {

            store,

        };
    },

    created() {
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0').then((res) => {

            // console.log(res.data.data);

            this.store.cards = res.data.data;

            console.log(this.store.cards);
        });
    },

    components: {
        CardsItem,
    }
};


</script>

<template>
    <div id="cards-container">

        <CardsItem v-for="card in store.cards" :card="card"></CardsItem>

    </div>
</template>

<style lang="scss" scoped>
#cards-container {
    max-width: 1100px;
    margin: 0 auto;
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
}
</style>