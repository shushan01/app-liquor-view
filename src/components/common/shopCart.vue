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
            position: absolute;
            left: 18%;
            top: 3px;
        }
    }

</style>
<template>
    <div class="shop-cart">
        <i></i>
        <span class="counter">
        <mt-badge type="error" size="small">{{shopCount}}</mt-badge>
        </span>
        <ShopCartBalls ref="ball" :getPosition="false"></ShopCartBalls>
    </div>
</template>

<script>
    import ShopCartBalls from 'common/shopCartBalls';
    import {Badge} from 'mint-ui';

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
