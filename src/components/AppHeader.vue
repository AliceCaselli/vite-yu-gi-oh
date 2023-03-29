<script>

name: 'AppHeader';

export default {
    data() {
        return {

            links: [
                'the game',
                'the cards',
                'the story',

            ],
        };
    },
};
</script>

<template>
    <header>

        <div id="header-container">

            <div id="logo">
                <img src="/images/logo.png" alt="">

            </div>

            <div id="list">
                <ul>
                    <li v-for="link in links">{{ link }}</li>
                </ul>
            </div>
        </div>
    </header>
</template>

<style lang="scss" scoped>
header {
    width: 100vw;
    background-color: #f6f6f6;


    #header-container {
        max-width: 1100px;
        margin: 0 auto;
        display: flex;
        flex-direction: row;
        justify-content: space-between;

        #list {
            display: flex;
            flex-direction: row;
            align-items: center;

            ul {
                width: 100%;
                display: flex;
                flex-direction: row;
                gap: 50px;

                color: black;
                list-style-type: none;
                text-transform: uppercase;
                font-weight: bold;
            }
        }
    }
}
</style>