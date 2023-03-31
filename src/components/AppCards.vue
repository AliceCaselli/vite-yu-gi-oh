<script>

import { store } from "../store.js";
import axios from "axios";
import CardsItem from "./CardsItem.vue";
import AppSearch from "./AppSearch.vue";
import AppCount from "./AppCount.vue";
import AppLoader from "./AppLoader.vue";

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
            this.store.isLoading = false;
        });
    },

    components: {
        CardsItem,
        AppSearch,
        AppCount,
        AppLoader,
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
                    this.store.isLoading = false;

                }).catch((err) => {

                    alert('No match found');
                    this.store.searchWord = '';
                    this.store.isLoading = false;

                });
            } else {
                axios.get(this.store.APIcall).then((res) => {
                    this.store.cards = res.data.data;
                    this.store.isLoading = false;
                });
            };
        },
    },
}


</script>

<template>
    <AppSearch @research="search()"></AppSearch>
    <AppLoader v-if="store.isLoading"></AppLoader>
    <AppCount></AppCount>
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