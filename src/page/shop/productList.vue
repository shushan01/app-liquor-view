<!-- productList -->
<style lang="scss" scoped>
    @import '~assets/common/css/mixin.scss';

    .product-root {
        .search-rusult-container {
            height: 100%;
            .search-top {
                @include flexbox(space-between,
                        center,
                        row,
                        nowrap);
                padding: 10px 20px;
                background: #fff;
                border-bottom: 1px solid #eee;
                .back-icon {
                    width: 23px;
                    height: 23px;
                    background: url('~jd/images/arrow-left.png') no-repeat;
                    background-size: 100%;
                }
                .searchInput {
                    width: 90%;
                    .search-box {
                        width: 100%;
                        position: relative;
                        background: #f4f4f4;
                        padding: 5px 10px;
                        border-radius: 10px;
                        @include flexbox(space-between,
                                center,
                                row,
                                nowrap);
                        input {
                            width: 100%;
                            color: #333;
                            font-size: $subtitle;
                            outline: none;
                            border: none;
                            box-shadow: none;
                            text-shadow: none;
                            font-weight: normal;
                            background: transparent;
                        }
                        .searchIcon {
                            display: block;
                            height: .38rem;
                            margin-right: .05rem;
                            width: .4rem;
                            background: url('~jd/images/searchIcon.png') no-repeat;
                            background-size: 600% 100%;
                            background-position: -0.34rem 0;
                        }
                    }
                }
                > span {
                    text-align: center;
                    font-size: 15px;
                    min-width: 1.5rem;
                    color: $gray;
                }
            }
            .search-filter {
                // border-top: 1px solid $border;
                border-bottom: 1px solid #eee;
                .search-filter-list {
                    background: #fff;
                    @include flexbox(space-between, center, row, nowrap);
                    .search-filter-item {
                        width: 25%;
                        @include flexbox(center, center, row, nowrap);
                        color: #333;
                        font-size: 15px;
                        padding: 12px 0;
                        &.active {
                            color: $red;
                        }
                        &.more-sort {
                            position: relative;
                            &:after {
                                content: '';
                                position: absolute;
                                right: .5rem;
                                top: 44%;
                                width: 0;
                                height: 0;
                                border: 5px solid transparent;
                                border-top-color: $red;
                            }
                        }
                    }
                }
            }
            .content {
                width: 100%;
                .product-list {
                    @include flexbox(flex-start, center, column, wrap);
                    .prod-item {
                        height: 125px;
                        position: relative;
                        width: 100%;
                        background: #fff;
                        @include flexbox(space-between, flex-start, row, nowrap);
                        padding: 5px 0px 0px 5px;
                        flex: initial;
                        img {
                            width: 125px;
                            height: 125px;
                        }
                        .prod-info {
                            height: 100%;
                            margin-left: 10px;
                            padding-right: 5px;
                            border-bottom: 1px solid #eee;
                            @include flexbox(space-between, flex-start, column, wrap);
                            .prod-title {
                                font-size: $title;
                                color: #333;
                                @include textoverflow(2);
                            }
                            .prod-price {
                                color: $red;
                                margin-top: 50px;
                                text-align: left;
                                span {
                                    font-size: $smsub;
                                    margin-right: 5px;
                                }
                                strong {
                                    font-size: 19px;
                                }
                            }
                            .prod-pro {
                                padding: 5px 0;
                                text-align: left;
                                color: $gray;
                                font-size: $subtitle;
                            }
                        }
                        .shop-cart {
                            position: absolute;
                            bottom: 10px;
                            right: 10px;
                            background-color: #da0808;
                            width: 25px;
                            height: 25px;
                            border-radius: 3px;
                            color: #fff;
                            .ye-icon-cart {
                                margin-left: 3px;
                                padding-top: 3px;
                            }
                        }
                    }
                }
            }
        }
        .product-footer {
            position: fixed;
            bottom: 10px;
            left: 10px;
            z-index: 5000;
            height: 40px;
            width: 30%;
            background-color: #333;
            opacity: 0.7;
            border-radius: 5px;
            .product-shop-left {
                width: 50%;
                height: 100%;
                border: 1px none #fff;
                border-right-style: solid;
                float: left;
                .ye-icon-cart {
                    color: #fff;
                    font-size: 26px;
                    padding-top: 5px;
                    padding-left: 7%;
                }
                .product-counter {
                    width: 18px;
                    height: 18px;
                    position: absolute;
                    background-color: #ff3300;
                    border-radius: 9px;
                    left: 24%;
                    top: 0px;
                    span {
                        left: 4px;
                        top: 1px;
                        position: absolute;
                        color: #fff;
                        font-size: 14px;
                    }
                }
            }
            .product-shop-right {
                .ye-icon-account {
                    color: #fff;
                    font-size: 26px;
                    padding-top: 5px;
                    padding-left: 46%;
                    margin-left: 16%;
                }
            }
        }
    }

</style>

<template>
    <div class="product-root" style="position:relative;">
        <div class="search-rusult-container" v-if="!searchVisiblie">
            <!-- 搜索框 -->
            <div class="search-top">
                <i class="back-icon" @click="$router.go(-1)"></i>
                <div class="searchInput">
                    <div class="search-box">
                        <i class="searchIcon searchContentIcon"></i>
                        <input placeholder="搜索商品、分类" @click="()=>searchVisiblie=true"></input>
                    </div>
                </div>
            </div>
            <!-- 搜索框 -->

            <!-- 筛选 -->
            <div class="search-filter">
                <ul class="search-filter-list">
                    <li class="search-filter-item active more-sort">销量</li>
                    <li class="search-filter-item">价格</li>
                    <li class="search-filter-item">筛选</li>
                </ul>
            </div>
            <!-- 筛选 -->

            <!-- 搜索内容 -->
            <div class="content">
                <load-more style="width:100%;" @loadMore="infiniteCallback" :commad="commad" :param="searchParams"
                           ref="searchRusultloadMore">
                    <ul class="product-list">
                        <li class="prod-item" v-for="(item,index) in searchRusultData" :key="index"
                            @click="()=>$router.push('/product/'+item.productNo)">
                            <img :src="item.image_url[0].url" alt="">
                            <div class="prod-info">
                                <p class="prod-title">{{item.productName}}</p>
                                <p class="prod-price"><span>&yen;</span><strong>{{item.price}}</strong></p>
                            </div>
                            <div class="shop-cart" @click.stop="addShopCart($event)">
                                <div class="ye-icon-cart"></div>
                            </div>
                        </li>
                    </ul>
                </load-more>
            </div>
            <!-- 搜索内容 -->
            <BackHead/>
        </div>
        <SearchProduct :searchVisiblie="searchVisiblie" @cancel="()=>searchVisiblie=false"/>
        <div class="product-footer" v-if="!searchVisiblie">
            <div class="product-shop-left" @click="$router.push('/cart')">
                <div class="ye-icon-cart"/>
                <span class="product-counter">
                    <span>{{shopCount}}</span>
                </span>
                <ShopCartBalls ref="ball"></ShopCartBalls>
            </div>
            <div class="product-shop-right" @click="/*$router.push('/myhome')*/">
                <div class="ye-icon-account"></div>
            </div>
        </div>
    </div>
</template>

<script>
    import BackHead from 'common/backHead';
    import LoadMore from 'common/loadMore';
    import SearchProduct from 'common/searchProduct';
    import ShopCartBalls from 'common/shopCartBalls';
    import {
        searchGoods
    } from '@/service/getData'

    export default {
        data() {
            return {
                searchVisiblie: false,
                shopCount: 0,
                searchRusultData: [],
                commad: searchGoods,
                searchParams: {
                    Keyword: '',
                    pageSize: 10,
                    pageIndex: 1
                }
            };
        },

        watch: {
            'searchParams.Keyword': function (val) {
                this.searchRusult()
            }
        },

        components: {
            BackHead,
            ShopCartBalls,
            SearchProduct,
            LoadMore
        },

        computed: {},

        methods: {
            async searchRusult() {
                this.searchParams.pageSize = 10;
                this.searchParams.pageIndex = 1;
                this.searchParams = JSON.parse(JSON.stringify(Object.assign(this.searchParams, this.$route.query)))
                this.$refs.searchRusultloadMore.onloadMoreScroll();
            },
            async infiniteCallback(response) { //下拉加载
                if (response.Data.length > 0) {
                    let baseUrl = "http://yangs2.tunnel.qydev.com/src/assets/test/img";
                    var j = 0;
                    response.Data.map(i => {
                        j++;
                        if (i.image_url[0]) {
                            i.productNo = "963652948422340";
                            if (j % 2 == 0) {
                                i.productName = "飞天茅台 53°酱香型 500ml";
                                i.image_url[0].url = baseUrl + "/product01.jpg";
                            } else {
                                i.productName = "洋河蓝色经典·梦之蓝 M3  52° 绵柔型 500ml";
                                i.image_url[0].url = baseUrl + "/product02.jpg";
                            }
                            this.searchRusultData.push(i)
                        }
                    })
                }
            },
            async addShopCart(target) { //加入购物车
                this.$refs.ball.drop(target);
                this.shopCount++;
            },
        },

        mounted: function () {
            this.searchParams = JSON.parse(JSON.stringify(Object.assign(this.searchParams, this.$route.query)))
            this.$refs.searchRusultloadMore.onloadMoreScroll();
        }
    }

</script>