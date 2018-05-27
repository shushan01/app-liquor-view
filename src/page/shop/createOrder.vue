<!-- createdOrder -->
<style lang="scss" scoped>
    @import '~assets/common/css/mixin.scss';

    .pagePay {
        .my-header {
            padding: $padding;
            background: #fff;
            @include flexbox(space-between, center, row, nowrap);
            border-bottom: 1px solid #eee;
            .back {
                display: block;
                width: .65rem;
                height: .65rem;
                background: url('~jd/images/arrow-left.png') no-repeat;
                background-size: 100%;
            }
            strong {
                font-size: 18px;
                font-weight: normal;
                color: #333;
            }
            .myMsg {
                display: block;
                background: url('~jd/images/searchIcon.png') no-repeat;
                background-size: 600% 100%;
                height: .65rem;
                width: .65rem;
                opacity: 0;
                background-position: -2.6rem 0;
            }
        }
        .payContainer {
            .venderOrderList {
                margin-top: $margin;
                .venderItem {
                    padding: $padding;
                    border-bottom: 1px solid #eee;
                    background: #fff;
                    @include flexbox(flex-start,
                            center,
                            row,
                            nowrap);
                    img {
                        max-width: 1.6rem;
                        max-height: 1.6rem;
                        margin: 10px;
                        padding-right: 10px;
                    }
                    .orderInfo {
                        @include flexbox(space-between,
                                flex-start,
                                column,
                                wrap);
                        font-size: 16px;
                        .title {
                            @include textoverflow(1);
                            margin-bottom: 25px;
                        }
                        .price {
                            @include flexbox(space-between,
                                    center,
                                    row,
                                    nowrap);
                            width: 100%;
                            .fee {
                                color: $red;
                            }
                            .count {
                                font-size: 14px;
                                color: #999;
                            }
                        }
                    }
                }
                .order-footer {
                    width: 100%;
                    text-align: right;
                    line-height: 30px;
                    font-size: 16px;
                    padding: 5px;
                    background: #fff;
                }
                .pay-typ {
                    width: 100%;
                    background: #fff;
                    margin-top: 10px;
                    font-size: 16px;
                    .left {
                        width: 50%;
                        float: left;
                        font-weight: 600;
                        padding: 5px;
                        line-height: 40px;
                    }
                    .right {
                        display: inline-block;
                        width: 50%;
                        padding: 5px;
                        text-align: right;
                    }
                }
            }
        }
        .payOnline {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            width: 100%;
            background: #fff;
            font-size: 17px;
            @include flexbox(flex-end,
                    center,
                    row,
                    nowrap);
            span {
                width: 60%;
                color: $red;
                padding: 0 $padding;
            }
            .payBtn {
                width: 40%;
                height: 100%;
                color: #fff;
                padding: 15px;
                background: $red;
                text-align: center;
            }
        }
    }
</style>
<template>
    <div class="pagePay">
        <div class="my-header">
            <i class="back" @click="$router.go(-1)"></i>
            <strong>确认订单</strong>
            <i class="myMsg"></i>
        </div>
        <div class="payContainer">
            <div class="venderOrderList" v-if="confirmSelectedProduct">
                <div class="venderItem" v-for="(item,index) in confirmSelectedProduct" :key="index">
                    <img :src="item.product.image_url[0].url" alt="">
                    <div class="orderInfo">
                        <p class="title">{{item.product.productName}}</p>
                        <div class="price">
                            <span class="fee">&yen;
                              <strong>{{item.product.price}}</strong>
                            </span>
                            <span class="count">x {{item.counter}}</span>
                        </div>
                    </div>
                </div>
                <div class="order-footer">
                    <span>共 {{counter}} 件商品  合计：&yen;{{totalFee}}</span>
                </div>
                <div class="pay-typ">
                    <div class="left"><span style="color: red">*</span>支付方式</div>
                    <div class="right">
                        <i>
                            <img src="~jd/images/weixin.png">
                        </i>
                    </div>
                </div>
            </div>
            <p v-else style="text-align:center;padding:15px 0; color:#999;font-size:17px;">
                暂无数据
            </p>
        </div>
        <div class="payOnline">
            <span>应付金额：&yen;{{totalFee}}</span>
            <div class="payBtn" @click="submitOrder">提交订单</div>
        </div>
    </div>
</template>

<script>
    import {
        Field,
        Button,
        Toast,
        Popup
    } from 'mint-ui';
    import {
        mapGetters
    } from 'vuex'

    export default {
        data() {
            return {
                totalFee: 0.00,
                counter: 0,
                confirmSelectedProduct: null
            };
        },

        watch: {},

        components: {},

        computed: {
            ...mapGetters([
                'addressList'
            ])
        },

        methods: {
            async initData() {
                // let confirmSelectedData = await this.$store.dispatch('GetConfirmSelectedProductList', {})
                let confirmSelectedProduct = [{
                    product: {
                        image_url: [{
                            url: "http://yangs2.tunnel.qydev.com/src/assets/test/img/product01.jpg"
                        }],
                        productName: "飞天茅台 53°酱香型 500ml",
                        summary: "香醇可口",
                        price: 998,
                        productNo: 963652948422340
                    },
                    counter: 2
                },
                    {
                        product: {
                            image_url: [{
                                url: "http://yangs2.tunnel.qydev.com/src/assets/test/img/product02.jpg"
                            }],
                            productName: "洋河蓝色经典·梦之蓝 M3  52° 绵柔型 500ml",
                            summary: "海之蓝",
                            price: 668,
                            productNo: 963652948422340
                        },
                        counter: 1
                    }
                ];
                if (confirmSelectedProduct.length == 0) {
                    Toast({
                        message: '暂无订单信息'
                    })
                    return this.$router.go(-1);
                }
                confirmSelectedProduct.map(item => {
                    this.totalFee += item.counter * item.product.price;
                    this.counter += item.counter;
                })
                this.totalFee = this.totalFee.toFixed(2);
                this.confirmSelectedProduct = confirmSelectedProduct;
            },
            async submitOrder() {
                Toast({
                    message: '未开发'
                })
            },
        },

        mounted: function () {
            this.initData();
        }
    }

</script>