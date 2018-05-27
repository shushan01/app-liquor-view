<!-- product -->
<style lang="scss" scoped>
    @import '~assets/common/css/mixin.scss';
    /* 顶部导航栏 */

    .product-header {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        z-index: 9999;
        height: 1.25rem;
        background: #fff;
        border-bottom: 1px solid $border;
        .product-header-container {
            height: 100%;
            padding: 0px $padding;
            @include flexbox(space-between, center, row, nowrap);
            .goback {
                i {
                    display: block;
                    width: .65rem;
                    height: .65rem;
                    background: url('~jd/images/arrow-left.png') no-repeat;
                    background-size: 100%;
                }
            }
            .product-tabs {
                margin-left: 30px;
                height: 100%;
                @include flexbox(space-between,
                        center,
                        row,
                        nowrap);
                position: relative;
                #loadingbar {
                    position: absolute;
                    transition: .4s;
                    width: calc((100% / 3));
                    background: #000;
                    bottom: -1px;
                    height: 2px;
                }
                .product-tabs-item {
                    width: 50%;
                    @include flexbox(center,
                            center,
                            row,
                            nowrap);
                    flex: initial;
                    text-align: center;
                    color: #333;
                    font-size: $subtitle;
                    height: 100%;
                    &.active {
                        font-size: $title;
                    }
                }
            }
        }
    }

    /* 顶部导航栏 */

    /* 商品 */

    #mainLayout {
        .prouct-swiper {
            box-shadow: 0px 0px 6px 1px #eee;
            position: relative;
            .swiper-indicators {
                font-size: $title;
                z-index: 666;
                position: absolute;
                width: 40px;
                height: 40px;
                border-radius: 50%;
                -webkit-border-radius: 50%;
                background: rgba(0, 0, 0, .15);
                right: 15px;
                bottom: 11px;
                text-align: center;
                line-height: 40px;
                color: #fff;
                overflow: hidden;
            }
            .scroll-images {
                height: 10rem;
                img {
                    width: 100%;
                    vertical-align: middle;
                    max-height: 10rem;
                    min-height: 10rem;
                }
            }
        }
        .product-title-text {
            @include flexbox(space-between,
                    flex-start,
                    column,
                    wrap);
            padding: $padding;
            background: #fff;
            .product-name-text {
                font-size: $title;
                color: #232326;
                @include textoverflow(2);
            }
            .product-summary-text {
                font-size: $subtitle;
                padding: 5px 0;
                color: #f23030;
                line-height: 1.6;
                @include textoverflow(2);
            }
            .product-price {
                margin-top: 10px;
                color: #f23030;
                text-align: left;
                width: 100%;
                span {
                    font-size: 14px;
                    margin-right: 5px;
                }
                strong {
                    font-size: 23px;
                }
            }
        }
        .product-sku {
            margin-top: $margin;
            background: #fff;
            padding: $padding;
            @include flexbox(space-between,
                    center,
                    row,
                    nowrap);
            .sku-select {
                font-size: $subtitle;
                color: #999;
                margin-right: 5px;
            }
            .sku-info {
                font-size: $subtitle;
                color: #232326;
            }
            .right-menu {
                width: 19px;
                height: 4px;
                background-image: url('~jd/images/product-detail-sprites-mjs.png');
                background-repeat: no-repeat;
                background-size: 100px 100px;
                background-position: -42px -17px;
            }
        }
        .product-comment {
            margin-top: $margin;
            padding: $padding;
            background: #fff;
            @include flexbox(space-between,
                    center,
                    column,
                    wrap);
            .comment-info {
                width: 100%;
                padding: 0 0 $padding;
                border-bottom: 1px solid $border;
                @include flexbox(space-between,
                        center,
                        row,
                        nowrap);
                flex: initial;
                .comment-num {
                    font-size: $subtitle;
                    color: $gray;
                }
                .comment-percentage {
                    strong {
                        color: $red;
                        font-size: $subtitle;
                        margin-left: 5px;
                        font-weight: normal;
                    }
                }
            }
            .comment-list {
                padding: $padding 0;
                width: 100%;
                .comment-item {
                    .comment-more {
                        @include flexbox(center,
                                center,
                                row,
                                nowrap);
                        font-size: $subtitle;
                        color: $gray;
                        width: 100%;
                        padding: $padding 0;
                        border-radius: 5px;
                        border: 1px solid #eeeeee;
                    }
                    @include flexbox(space-between,
                            flex-start,
                            column,
                            wrap);
                    flex: initial;
                    width: 100%;
                    border-bottom: 1px solid $gray;
                    &:last-child {
                        border-bottom: none;
                    }
                    .comment-userinfo {
                        width: 100%;
                        @include flexbox(space-between,
                                center,
                                row,
                                nowrap);
                        display: inline-flex;
                        padding: 5px 0;
                        img {
                            width: 30px;
                            height: 30px;
                            border-radius: 50%;
                            overflow: hidden;
                        }
                        .avatar {
                            @include flexbox(flex-satrt,
                                    center,
                                    row,
                                    nowrap);
                            flex: initial;
                            span {
                                font-size: $smsub;
                                color: #333;
                                vertical-align: text-top;
                                margin-left: 5px;
                            }
                        }
                        .comment-star {
                            @include flexbox(flex-end,
                                    center,
                                    row,
                                    nowrap);
                            .star-item {
                                display: block;
                                width: 14px;
                                height: 14px;
                                background: url('~jd/images/star-h.png') no-repeat;
                                background-size: 100%;
                            }
                        }
                    }
                    .comment-content {
                        @include flexbox(space-between,
                                flex-start,
                                column,
                                wrap);
                        width: 100%;
                        .content {
                            font-size: $subtitle;
                            color: #333;
                            @include textoverflow(2);
                            padding: $padding 0;
                        }
                        .comment-images-list {
                            @include flexbox(space-between,
                                    center,
                                    row,
                                    nowrap);
                            margin-bottom: $margin;
                            img {
                                width: 84px;
                                margin-right: 5px;
                                height: 84px;
                                &:last-child {
                                    margin-right: 0;
                                }
                            }
                        }
                    }
                    .comment-sku {
                        text-align: left;
                        color: $gray;
                        font-size: $smsub;
                        margin-bottom: $margin;
                    }
                }
            }
        }
        .goods-part {
            margin-top: $margin;
            background: #fff;
            padding: $padding;
            @include flexbox(space-between,
                    center,
                    column,
                    wrap);
            > div {
                width: 100%;
            }
            .goods-part-info {
                @include flexbox(flex-start,
                        center,
                        row,
                        nowrap);
                flex: initial;
                img {
                    width: 80px;
                    height: 26px;
                    border: 1px solid $border;
                }
                > div {
                    margin-left: 10px;
                    @include flexbox(space-between,
                            flex-start,
                            column,
                            wrap);
                    flex: initial;
                    .goods-part-title {
                        font-size: $title;
                        color: #333;
                        @include textoverflow(1);
                    }
                    .goods-part-summary {
                        color: $gray;
                        margin-top: 5px;
                        font-size: $smsub;
                        @include textoverflow(1);
                    }
                }
            }
            .good-part-quantity {
                @include flexbox(space-between,
                        center,
                        row,
                        nowrap);
                padding: 15px 0;
                > div {
                    width: 33.33%;
                    border-right: 1px solid $border;
                    @include flexbox(space-between,
                            center,
                            column,
                            wrap);
                    &:last-child {
                        border-right: none;
                    }
                    strong {
                        font-size: $title;
                        color: #333;
                        text-align: center;
                        font-weight: normal;
                    }
                    span {
                        text-align: center;
                        color: $gray;
                        margin-top: 5px;
                        font-size: $smsub;
                    }
                }
            }
            .good-part-service {
                @include flexbox(space-between,
                        center,
                        row,
                        nowrap);
                > div {
                    border: 1px solid $border;
                    border-radius: 2px;
                    width: 49%;
                    text-align: center;
                    padding: 6px 0;
                    span {
                        text-align: center;
                        font-size: $subtitle;
                        margin-left: 5px;
                        vertical-align: 0.1rem;
                        color: $gray;
                    }
                    i {
                        display: inline-block;
                        background-size: 100px 100px;
                        background-repeat: no-repeat;
                        background-image: url('~jd/images/product-detail-sprites-mjs.png');
                    }
                }
                .good-part-contact {
                    i {
                        width: 18px;
                        height: 18px;
                        background-position: -30px -48px;
                    }
                }
                .go-good-part {
                    i {
                        width: 18px;
                        height: 18px;
                        background-position: -83px -48px;
                    }
                }
            }
        }

        .count-container {
            padding: $padding;
            background-color: #fff;
            margin-top: 5px;
            font-size: 16px;
            font-weight: 700;
        }
    }

    /* 商品 */

    /* 底部导航栏 */

    .cart-concern-fixed {
        position: fixed;
        bottom: -1px;
        left: 0;
        right: 0;
        width: 100%;
        height: 1.25rem;
        background: #fff;
        border-top: 1px solid $border;
        @include flexbox(space-between,
                center,
                row,
                nowrap);
        .left {
            width: 35%;
            height: 100%;
            @include flexbox(space-between,
                    center,
                    row,
                    nowrap);
            flex: initial;
            > div {
                margin-left: 30%;
                width: 33.33%;
                @include flexbox(space-between,
                        center,
                        column,
                        wrap);
                flex: initial;
                span {
                    color: #333;
                    font-size: $smsub;
                    margin-top: 2px;
                }
                i {
                    display: block;
                    width: 23px;
                    height: 23px;
                }
            }
            .like-icon {
                i {
                    background: url('~jd/images/cart_sprits_all.png') no-repeat;
                    background-position: -50px 0;
                    background-size: 100px 100px;
                    &.active {
                        background-size: -50px -21px;
                    }
                }
            }
        }
        .center {
            width: 30%;
            height: 100%;
            background: #FF9933;
            color: #fff;
            font-size: $title;
            @include flexbox(center,
                    center,
                    row,
                    nowrap);
            flex: initial;
        }
        .right {
            width: 35%;
            height: 100%;
            background: #e4393c;
            color: #fff;
            font-size: $title;
            @include flexbox(center,
                    center,
                    row,
                    nowrap);
            flex: initial;
        }
    }

    /* 底部导航栏 */
</style>
<style lang="scss">
    #prodContent-container {
        width: 100%;
        clear: both;
        overflow: hidden;
    }

    #prodContent-container * {
        max-width: 100% !important;
        width: 100% !important;
        height: auto !important;
    }

</style>

<template>
    <div style="background:#f8f8f8;">
        <!-- 顶部导航栏 -->
        <div class="product-header">
            <div class="product-header-container">
                <div class="goback" @click="$router.go(-1)">
                    <i class="back"></i>
                </div>
                <div class="product-tabs">
                    <span @click="switchTabs('mainLayout')"
                          :class="['product-tabs-item',containerTab==='mainLayout'?'active':'']">商品</span>
                    <span @click="switchTabs('goodDetail')"
                          :class="['product-tabs-item',containerTab==='goodDetail'?'active':'']">详情</span>
                    <div id="loadingbar"
                         :style="containerTab==='mainLayout' ? 'left:7%' : 'left:58%'"></div>
                </div>
            </div>
        </div>
        <!-- 顶部导航栏 -->
        <!-- 内容区 -->
        <mt-tab-container v-model="containerTab" :swipeable="true" style="margin: 1.25rem 0 0 0;">
            <!-- 商品 -->
            <mt-tab-container-item id="mainLayout" v-if="containerTab==='mainLayout'">
                <div id="mainLayout">
                    <!-- 商品轮播图 -->
                    <div class="prouct-swiper">
                        <mt-swipe @change="handleChange" :showIndicators="false" :stopPropagation="true"
                                  :prevent="true" :continuous="false" :auto="0"
                                  class="scroll-images">
                            <mt-swipe-item v-for="(item,index) in productInfo.image_url" :key="index">
                                <img :src="item.url" :alt="item.name">
                            </mt-swipe-item>
                        </mt-swipe>
                        <div class="swiper-indicators">{{swipeIndex.nowIndex}}/{{swipeIndex.total}}</div>
                    </div>
                    <!-- 商品轮播图 -->
                    <!-- 商品信息 -->
                    <div class="product-title-text">
                        <p class="product-name-text">{{productInfo.productName}}</p>
                        <div class="product-price">
                            <span>&yen;</span>
                            <strong>{{productInfo.price}}</strong>
                        </div>
                    </div>

                    <div class="count-container">
                        数量：
                        <Counter ref="count"></Counter>
                    </div>

                </div>
            </mt-tab-container-item>
            <!-- 商品详情 -->
            <mt-tab-container-item id="goodDetail">
                <div id="goodDetail">

                </div>
            </mt-tab-container-item>
            <!-- 商品详情 -->
            <!-- 商品 -->
        </mt-tab-container>
        <!-- 内容区 -->

        <!-- 底部导航栏 -->
        <div class="cart-concern-fixed">
            <div class="left">
                <div class="shopping-cart" @click="$router.push('/cart')">
                    <ShopCart ref="cart" :shopCount="shopCount"></ShopCart>
                </div>
            </div>
            <div class="center" @click="addShopCart">加入购物车</div>
            <div class="right" @click="$router.push('/createOrder');">立即购买</div>
        </div>
        <!-- 底部导航栏 -->

        <!-- 返回顶部 -->
        <BackHead/>
        <!-- 返回顶部 -->
    </div>
</template>

<script>
    import {
        Swipe,
        Toast,
        SwipeItem
    } from 'mint-ui';
    import {
        getProduct,
        getShop
    } from '@/service/getData'
    import {
        getLocalStorage,
        setLocalStorage
    } from '@/utils/mixin';
    import BackHead from 'common/backHead';
    import Counter from 'common/counter';
    import ShopCart from 'common/shopCart';

    export default {
        data() {
            return {
                shopCount: 0,
                containerTab: 'mainLayout',
                productInfo: {},
                swipeIndex: {
                    nowIndex: 1,
                    total: 0
                },
                commentParam: {
                    ProductNo: null,
                    pageSize: 10,
                    pageIndex: 1
                },
            };
        },

        watch: {
            '$route.params': function () {
                this.setCount()
            }
        },

        components: {
            Swipe,
            SwipeItem,
            Counter,
            ShopCart,
            BackHead
        },

        computed: {},

        methods: {
            switchTabs(Id) {
                if (this.containerTab === String(Id)) return;
                this.containerTab = Id;
                switch (String(this.containerTab)) {
                    case 'mainLayout':
                        break;
                    case 'goodDetail':
                        break;
                    default: //其他
                        throw new Error('未知TabId')
                        break
                }
            },
            handleChange(index) {
                this.swipeIndex.nowIndex = index + 1;
            },
            async addShopCart(target) { //加入购物车
                this.$refs.cart.drop(target);

                let count = getLocalStorage("cart-count");
                this.shopCount = parseInt(count) + this.$refs.count.number;
                setLocalStorage("cart-count", this.shopCount + "");
            },
            async initData() {
                this.setCount();
                this.commentParam.ProductNo = this.$route.params.id;
                let {
                    Data
                } = await getProduct({
                    ProductNo: this.$route.params.id
                });
                Data.price = Data.price.toFixed(2);
                Data.productName = "飞天茅台 53°酱香型 500ml";
                let baseUrl = "http://yangs2.tunnel.qydev.com/src/assets/test/img";
                Data.image_url[0].url = baseUrl + "/product01.jpg";
                Data.image_url[1].url = baseUrl + "/product02.jpg";
                this.productInfo = Data;
                this.swipeIndex.total = Data.image_url.length;
            },
            async setCount() {
                let count = getLocalStorage("cart-count");
                if (count) {
                    this.shopCount = parseInt(count);
                }
            }
        },

        mounted: function () {
            this.initData();
        }
    }

</script>
