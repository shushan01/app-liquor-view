<!-- searchRusult -->
<style lang="scss" scoped>
    @import '~assets/common/css/mixin.scss';

    .shop-cart {
        i {
            background: url('~jd/images/cart_sprits_all.png') no-repeat;
            background-position: 0 -21px;
            background-size: 100px 100px;
            display: block;
            width: 23px;
            height: 23px;
            margin-left: 5px;
        }
        .counter {
            width: 18px;
            height: 18px;
            position: absolute;
            background-color: #ff3300;
            border-radius: 9px;
            left: 18%;
            top: 3px;
            span {
                left: 32%;
                position: absolute;
                color: #fff;
                font-size: 14px;
            }
        }
    }

</style>
<template>
    <div class="shop-cart">
        <i></i>
        <span class="counter">
        <span>{{shopCount}}</span>
        </span>
        <ShopCartBalls ref="ball" :getPosition="false"></ShopCartBalls>
    </div>
</template>

<script>
    import ShopCartBalls from 'common/shopCartBalls';

    export default {
        data() {
            return {
                Keyword: '',
                searchHistoryData: [],
                searchRusultData: []
            };
        },
        props: {
            shopCount: {
                default: 0,
                type: Number
            }
        },
        components: {
            ShopCartBalls
        },

        computed: {},

        methods: {
            drop(target) {
                this.$refs.ball.drop(target);
            }
        },

        mounted: function () {
            try {
                this.searchHistoryData = JSON.parse(getLocalStorage('searchHistoryData'));
            } catch (err) {
            }
        }
    }

</script>
