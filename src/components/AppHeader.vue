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

            activeIndex: -1,
        };
    },

    methods: {
        classActive(clickIndex) {
            this.activeIndex = clickIndex;
        }
    }
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
                    <li v-for="(link, index) in links" :class="activeIndex == index ? 'active' : ''"
                        @click="classActive(index)">{{ link }}</li>
                </ul>
            </div>
        </div>
    </header>
</template>

<style lang="scss" scoped>
header {
    background-color: #f6f6f6;


    #header-container {
        max-width: 1100px;
        margin: 0 auto;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;



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

                li {
                    height: 100%;
                    position: relative;

                    &.active {

                        color: #e11e1c;

                        &::before {
                            content: '';
                            position: absolute;
                            bottom: 0;
                            width: 100%;
                            height: 3px;
                            background-color: #e11e1c;
                        }
                    }
                }

                li:hover {
                    cursor: pointer;
                    color: #e11e1c;


                }
            }
        }
    }
}
</style>