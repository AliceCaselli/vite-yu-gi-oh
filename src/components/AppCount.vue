<script>
import { store } from "../store.js";

export default {
    name: 'AppCount',
    data() {
        return {

            store,
        };
    },
};

</script>

<template>
    <div>Carte trovate {{ this.store.cards.length }}</div>
</template>

<style lang="scss" scoped>
div {
    text-align: center;
    margin-top: 30px;
    font-size: 1.5em;
    font-weight: bold;
}
</style>