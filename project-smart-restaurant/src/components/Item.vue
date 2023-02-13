<template>
    <div class="item">
        <div class="item--tag" v-if="item.offer">Oferta</div>
        <img class="item--img" src="../assets/img/burguer.png" alt="">
        <div class="content">
            <h2 class="item--name">{{ item.name }}</h2>
            <p class="item--description">{{ item.description }}</p>
            <p class="item--price"> {{ currency }} </p>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Item',
    props: {
        item: {},
    },
    computed: {
        currency() {
            let val = ((`R$ ${this.item.price}`).replace('.', ','))
            return val
        }
    }
}
</script>
<style lang="less" scoped>
@import '../assets/variables.less';

    .item {
        width: 215.95px;
        height: 290px;
        border-radius: 8px;
        background-color: white;
        position: relative;
        margin: 20px;
        padding: 20px;

        &--tag {
            position: absolute;
            background-color: @pink;
            border-radius: 8px;
            color: white;
            top: 15px;
            right: 15px;
            font-weight: 500;
            font-size: 12px;
            padding: 3px 8px;
        }

        &--img {
            display: block;
            margin: 20px auto;
        }

        &--name {
            font-weight: 600;
            font-size: 18px;

        }

        &--description {
            color: @dark-grey;
            font-weight: 300;
            font-size: 12px;
            margin: 8px auto;
        }

        &--price {
            font-weight: 600;
            font-size: 18px;
            color: @light-yellow;
        }

        
        @media (max-width: 768px) {
            width: 100%;
            height: fit-content;
            border: 1px solid @light-grey;
            display: flex;
            margin: 13px auto;

            &--img {
                height: 60px;
                margin-right: 15px;
            }

            &--price {
                text-align: right;
                margin: 0 auto;
            }

        }
    }
</style>