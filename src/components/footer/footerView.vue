<!-- footer -->
<style lang='scss' scoped>
    .nav-bar {
        position: fixed;
        width: 10rem;
        margin: 0 auto;
        bottom: -1px;
        left: 0;
        right: 0;
        height: 1.35rem;
        padding: .066667rem 0 0;
        background: #fff;
        overflow: hidden;
        clear: both;
        box-shadow: 0px 0px 20px -8px #999;
        display: flex;
        flex: 1;
        z-index: 5000;
        justify-content: flex-start;
        align-items: center;
        flex-direction: row;
        flex-wrap: nowrap;
        border-top: 1px solid #eee;
        .barIcon {
            width: 2rem;
            height: 100%;
            cursor: pointer;
            background: url('~jd/images/navbar.png') 0 0 no-repeat;
            background-size: 850% 105%;
        }
        .barIcon2 {
            width: 2rem;
            height: 100%;
            cursor: pointer;
            background: url('~jd/images/footer.png') 0 0 no-repeat;
            background-size: 420% 115%;
        }
        .home {
            background-position: .1rem -0.07rem;
            &.active {
                background-position: -1.585rem -0.05rem;
            }
        }
        .category {
            background-position: 0rem -0.1rem;
            &.active {
                background-position: -4.14rem -0.1rem;
            }
        }
        .find {
            background-position: -2.0rem -0.1rem;
            &.active {
                background-position: -6.14rem -0.1rem;
            }
        }
        .cart {
            position: relative;
            background-position: -10rem -0.075rem;
            &.active {
                background-position: -11.7rem -0.075rem;
            }
            .product-counter {
                right: 13px;
                top: 0px;
                position: absolute;
            }
        }
        .myHome {
            background-position: -13.45rem -0.075rem;
            &.active {
                background-position: -15.15rem -0.075rem;
            }
        }
    }

</style>
<template>
    <ul class="nav-bar fool">
        <li :class="['barIcon','home',$route.name==='index'?'active':'']" @click="$router.push('/index')"></li>
        <li :class="['barIcon2','category',$route.name==='drinks'?'active':'']"
            @click="/*$router.push('/drinks')*/"></li>
        <li :class="['barIcon2','find',$route.name==='article'?'active':'']" @click="/*$router.push('/article')*/"></li>
        <li :class="['barIcon','cart',$route.name==='cart'?'active':'']" @click="$router.push('/cart')">
            <span class="product-counter">
                <mt-badge type="error" size="small">{{shopCount}}</mt-badge>
            </span>
        </li>
        <li :class="['barIcon','myHome',$route.name==='myhome'?'active':'']" @click="/*$router.push('/myhome')*/"></li>
    </ul>
</template>

<script>
    import {Badge} from 'mint-ui';
    import {
        getLocalStorage,
        setLocalStorage
    } from '@/utils/mixin';

    export default {
        data() {
            return {
                shopCount: 0
            };
        },

        watch: {
            '$route.params': function () {
                this.setCount()
            }
        },

        components: {},

        computed: {},

        methods: {
            async setCount() {
                let count = getLocalStorage("cart-count");
                if (count) {
                    this.shopCount = parseInt(count);
                }
            }
        },

        mounted: function () {
            this.setCount();
        }
    }

</script>
