<script>

import { store } from "../store.js";
import axios from "axios";
import CardsItem from "./CardsItem.vue";
import AppSearch from "./AppSearch.vue";
export default {
    data() {
        return {

            store,

        };
    },

    created() {
        axios.get(this.store.APIcall).then((res) => {

            // console.log(res.data.data);

            this.store.cards = res.data.data;

            console.log(this.store.cards);
        });
    },

    components: {
        CardsItem,
        AppSearch,
    },

    methods: {
        search() {
            // console.log(this.store.APIcall + this.store.APIquery + this.store.searchWord);

            let newApi = this.store.APIcall + this.store.APIquery + this.store.searchWord;
            console.log(newApi);

            if (this.store.searchWord != '') {

                axios.get(newApi).then((res) => {

                    console.log(res.data.data);
                    this.store.cards = res.data.data;
                    this.store.searchWord = '';
                }).catch((err) => {

                    alert('No match found');
                    this.store.searchWord = '';

                });
            } else {
                axios.get(this.store.APIcall).then((res) => {
                    this.store.cards = res.data.data;

                });
            };
        },
    },
}


</script>

<template>
    <AppSearch @research="search()"></AppSearch>
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
    justify-content: center;
    gap: 20px;
}
</style>