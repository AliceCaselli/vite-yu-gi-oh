<script>

import { store } from "../store.js";
import axios from "axios";

export default {
    data() {
        return {

            store,
        };
    },

    created() {
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0').then((res) => {

            console.log(res.data.name);
        });
    },

};


</script>

<template>
    <div id="cards-container">

        <div class="card">

        </div>

    </div>
</template>

<style lang="scss" scoped></style>