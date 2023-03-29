<script>

name: 'CardsItem';

export default {
    data() {
        return {};
    },
    props: {

        card: Object,
    },
};
</script>

<template>
    <div class="card">
        <div class="name">{{ card.name }}</div>

        <div class="img">
            <img :src="card.card_images[0].image_url" alt="">
        </div>

    </div>
</template>

<style lang="scss" scoped>
.card {

    display: flex;
    flex-direction: column;
    gap: 20px;
    align-items: center;
    margin-top: 50px;

    width: calc(100% / 4 - 20px / 4 * 3);

    .name {
        font-size: 1em;
        font-weight: bold;
    }

    .img {

        img {
            width: 100%;
            border: 2px solid #d2d19b;
        }
    }
}
</style>