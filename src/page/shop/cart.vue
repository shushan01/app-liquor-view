<!-- cart -->
<style lang="scss" scoped>
    @import '~assets/common/css/mixin.scss';

    .cart-title {
        @include flexbox(center, center, row, nowrap);
        position: fixed;
        font-size: 16px;
        width: 100%;
        z-index: 9;
        height: 50px;
        background-color: #fff;
    }

    /* 购物车列表 */

    .Section {
        .goods {
            .tips {
                color: #fff;
                padding: 5px;
                width: 100%;
                height: 90px;
                background-color: #c30505;
                .top {
                    padding: 5px;
                    font-size: 20px;
                    font-weight: 700;
                    border-bottom: 1px solid #fff;
                    position: relative;
                    span {
                        color: #fff;
                        position: absolute;
                        right: 0;
                        top: 0;
                    }
                }
                .bottom {
                    padding: 5px;
                    font-size: 15px;
                    position: relative;
                    .switch {
                        position: absolute;
                        bottom: -20px;
                        right: 0;
                        div {
                            float: left;
                            width: 16px;
                            height: 16px;
                            border: 1px solid #fff;
                        }
                    }
                }
            }
            margin-top: 10px;
            @include flexbox(flex-start, space-between, column, wrap);
            background: linear-gradient(180deg, #fff, #efefef);
            .store-pd {
                @include flexbox(flex-start, space-between, column, wrap);
                background: #fff;
                flex: initial;
                .store-pd-item {
                    @include flexbox(flex-start, center, row, nowrap);
                    padding: 10px;
                    border-bottom: 1px solid #eee;
                    &:last-child {
                        border-bottom: none;
                    }
                    .pd-images {
                        border: 1px solid #eee;
                        margin: 0 15px 0 20px;
                        img {
                            width: 75px;
                            height: 75px;
                        }
                    }
                    .pd-info {
                        @include flexbox(flex-start, space-between, column, wrap);
                        width: 100%;
                        flex: initial;
                        .pd-title {
                            @include textoverflow(2); // width: 90%;
                            font-size: 13px;
                            color: #333;
                            p{
                                .product-name{
                                    padding-right: 15px;
                                }
                                position: relative;
                            }
                            .ye-icon-close{
                                position: absolute;
                                right: 0px;
                                top: 0px;
                            }
                        }
                        .pd-sku {
                            @include textoverflow(1);
                            padding: 5px 0;
                            line-height: 1.5;
                            font-size: 12px;
                            color: #999;
                        }
                        .pd-price {
                            margin-top: 10px;
                            @include flexbox(space-between, center, row, nowrap);
                            flex: initial;
                            .left {
                                color: #e93b3d;
                                span {
                                    font-size: 12px;
                                }
                                strong {
                                    font-size: 16px;
                                    font-weight: normal;
                                }
                            }
                            .right {
                                @include flexbox(space-between, center, row, nowrap);
                                flex: initial;
                                border-radius: 2px;
                                border: 1px solid #eee;
                                width: 2rem;
                                .cut {
                                    padding: 2px 0;
                                    font-size: 14px;
                                    text-align: center;
                                    width: 30%;
                                    height: .6rem;
                                    position: relative;
                                    cursor: pointer;
                                    &:before {
                                        content: '';
                                        position: absolute;
                                        right: 0;
                                        top: 0;
                                        background: #eee;
                                        width: 1px;
                                        height: 100%;
                                    }
                                    &:after {
                                        content: '';
                                        position: absolute;
                                        left: calc(100% / 2 - 5px);
                                        top: 50%;
                                        background: #999;
                                        width: 40%;
                                        height: 1px;
                                    }
                                }
                                .add {
                                    padding: 2px 0;
                                    width: 30%;
                                    height: .6rem;
                                    font-size: 14px;
                                    text-align: center;
                                    position: relative;
                                    cursor: pointer;
                                    &:before {
                                        content: '';
                                        position: absolute;
                                        left: 0;
                                        top: 0;
                                        background: #eee;
                                        width: 1px;
                                        height: 100%;
                                    }
                                    &:after {
                                        content: '+';
                                        position: absolute;
                                        left: calc(100% / 2 - 5px);
                                        top: calc(100% / 2 - 8px);
                                        font-size: 14px;
                                        color: #999; // width: 50%;
                                        // height: 1px;
                                    }
                                }
                                .num-inp {
                                    border: none;
                                    outline: none;
                                    text-align: center;
                                    padding: 0 5px;
                                    width: 40%;
                                    font-size: 12px;
                                }
                            }
                        }
                        .del-product {
                            margin-top: 10px;
                            @include flexbox(space-between, center, row, nowrap);
                        }
                    }
                }
            }
        }
        .cart-null {
            margin-top: 50px;
            text-align: center;
            font-size: 16px;
            color: #999;
            .cart-icon {
                display: inline-block;
                width: 20%;
                background: #ced0d1;
                font-size: 12px;
                position: relative;
                border-radius: 50%;
                vertical-align: middle;
                &:before {
                    content: "";
                    display: inline-block;
                    padding-bottom: 100%;
                    width: .1px;
                    vertical-align: middle;
                }
                .ye-icon-cart {
                    margin: 0 auto;
                    vertical-align: middle;
                    color: #fff;
                    font-size: 40px;
                }
            }
            p {
                padding: 5px 0;
            }
            .go-shop {
                background: #e4393c;
                width: 30%;
                height: 40px;
                border-radius: 3px;
            }
        }
    }

    /* 购物车列表 */

    /* 底部计算栏 */

    .section-bar {
        position: fixed;
        border-top: 1px solid #eee;
        bottom: 1.35rem;
        width: 100%;
        height: 1.25rem;
        @include flexbox(space-between, center, row, nowrap);
        .left {
            background: #fff;
            font-size: 12px;
            height: 100%;
            padding: 10px;
            width: 50%;
            @include flexbox(flex-start, center, row, nowrap);
            flex: initial;
            font-size: 13px;
            i {
                vertical-align: text-top;
                margin-right: 5px;
            }
            strong {
                margin-left: 10px;
                font-weight: normal;
                font-size: 17px;
                @include textoverflow(1);
            }
        }
        .center {
            width: 25%;
            height: 100%;
            color: #fff;
            font-size: 17px;
            background: #FF9933;
            @include flexbox(center, center, row, nowrap);
        }
        .right {
            width: 25%;
            height: 100%;
            background: #e4393c;
            color: #fff;
            @include flexbox(center, center, row, nowrap);
            strong {
                font-size: 17px;
                font-weight: normal;
                span {
                    font-size: 14px;
                }
            }
        }
    }

    /* 底部计算栏 */
</style>

<template>
    <div>
        <div class="cart-title">购物车</div>
        <!-- 购物车列表 -->
        <div class="Section">
            <load-more :style="{width:'100%',height: '85%',paddingTop: '1.2rem'}" :topMethod="onRefreshCallback"
                       :loadMoreIconVisible="false"
                       ref="cartLoadmore">
                <div class="goods">
                    <div class="tips" v-if="tipsVis">
                        <div class="top">
                            结算后会存入您的酒柜
                            <span class="ye-icon-close" @click="cancelTips"></span>
                        </div>
                        <div class="bottom">
                            把酒存入酒柜，随时随地提货、送礼、赞助酒局~
                            <div class="switch" @click="switchMethod">
                                <div>{{switchValue}}</div>
                                不再提示
                            </div>
                        </div>
                    </div>
                    <div class="store-pd" v-if="cartList&&cartList.length!=0">
                        <div class="store-pd-item" v-for="(item,index) in cartList" :key="index"
                             @click="()=>$router.push('/product/'+item.product.productNo)">
                            <i :class="['select-default-icon',item.checked ? 'select-icon' : '']"
                               @click.stop="checked(item)"></i>
                            <div class="pd-images">
                                <img :src="item.product.image_url[0].url" alt="">
                            </div>
                            <div class="pd-info">
                                <div class="pd-title">
                                    <p><span class="product-name">{{item.product.productName}}</span><span class="ye-icon-close" @click.stop="delCart(item.product.id)"></span></p>
                                </div>
                                <div class="pd-sku">
                                    <p class="sku-info">{{item.product.summary}}</p>
                                </div>
                                <div class="pd-price">
                                    <div class="left">
                                        <span>&yen;</span>
                                        <strong>{{item.product.price}}</strong>
                                    </div>
                                    <div class="right">
                                        <div class="cut" @click.stop="editProductNum({item:item,increment:-1})"></div>
                                        <input type="text" v-model="item.counter" class="num-inp"
                                               @change="editProductNum({item:item,counter:item.counter})"></input>
                                        <div class="add" @click.stop="editProductNum({item:item,increment:1})"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="cart-null" v-if="!cartList || cartList == ''">
                    <div class="cart-icon"><i class="ye-icon-cart"></i></div>
                    <p>
                        购物车还是空的
                    </p>
                    <p>
                        去挑几款好酒犒劳自己或者礼赠亲朋吧~
                    </p>
                    <mt-button type="danger" @click="$router.push(`/productList`)">选择商品</mt-button>
                </div>
            </load-more>
        </div>
        <!-- 购物车列表 -->
        <!-- 底部价格计算 -->
        <div class="section-bar" v-if="cartList&&cartList.length!=0">
            <div class="left">
                <i :class="['select-default-icon',selectedAll ? 'select-icon' : '']" @click="selectedAllGoods"></i>全选
                <strong>合计：&yen;{{totalFee}}</strong>
            </div>
            <div class="center" @click="emptyCart">
                清空
            </div>
            <div class="right" @click="confirmOrder">
                <strong>去结算
                    <span>({{selectedCounter}})</span>
                </strong>
            </div>
        </div>
        <!-- 底部价格计算 -->
        <FooterView/>
    </div>
</template>

<script>
    import FooterView from 'component/footer/footerView';
    import {
        Toast,
        Button
    } from 'mint-ui'
    import {
        setSessionStorage,
        getSessionStorage,
        getLocalStorage,
        setLocalStorage,
        removeSessionStorage
    } from '@/utils/mixin';
    import {
        mapGetters,
        mapMutations
    } from 'vuex';
    import LoadMore from 'common/loadMore';

    export default {
        data() {
            return {
                tipsVis: true,
                switchValue: "",
                cartList: null,
                totalFee: 0,
                selectedCounter: 0,
                selectedAll: false
            };
        },

        watch: {},

        components: {
            FooterView,
            LoadMore
        },

        computed: {
            ...mapGetters([
                'cartProductData',
                'userInfo'
            ])
        },

        methods: {
            selectedAllGoods() {
                this.cartList.map(item => {
                    item.checked = !this.selectedAll
                })
                this.selectedAll = !this.selectedAll;
                this.computedTotalFee();
            },
            confirmOrder() {
                let SelectedList = [];
                this.cartList.map(item => {
                    if (item.checked) {
                        SelectedList.push(item.product.productNo)
                    }
                })
                if (SelectedList == '') return Toast({
                    message: '请选择商品',
                    position: 'bottom'
                });
                /*this.$store.dispatch('ConfirmSelectProduct', {
                    SelectedList: JSON.stringify(SelectedList)
                }).then(response => {
                    this.$router.push('/createOrder');
                })*/
                this.$router.push('/createOrder');
            },
            computedTotalFee() {
                let computedFee = 0,
                    selectedCounter = 0;
                this.cartList.map(item => {
                    if (item.checked) {
                        computedFee += parseFloat(item.counter * item.product.price)
                        selectedCounter++
                    }
                })
                this.selectedCounter = selectedCounter;
                this.selectedAll = selectedCounter === this.cartList.length ? true : false;
                this.totalFee = computedFee.toFixed(2);
            },
            async editProductNum({item, increment, counter}) {
                let params = {
                    SelectedList: JSON.stringify([{
                        ProductNo: item.product.productNo
                    }])
                }
                if (counter) {
                    params.Counter = counter
                } else {
                    params.Increment = increment
                }
                // await this.$store.dispatch('SelectProduct', params)
                this.onRefreshCallback();
            },
            async checked(item) {
                item.checked = !item.checked;
                let count = 0;
                this.cartList.map(item => {
                    if (item.checked) return count++;
                })
                if (count === this.cartList.length) return this.selectedAllGoods();
                this.computedTotalFee();
            },
            async initData() {
                // let {
                //   Data
                // } = await this.$store.dispatch('GetSelectedProductList');
                let Data = {};
                this.cartList = [{
                    product: {
                        image_url: [{
                            url: "http://yangs2.tunnel.qydev.com/src/assets/test/img/product01.jpg"
                        }],
                        productName: "飞天茅台 53°酱香型 500ml",
                        summary: "香醇可口",
                        price: 998,
                        productNo: 963652948422340,
                        id:1
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
                            productNo: 963652948422340,
                            id:2
                        },
                        counter: 1
                    }
                ];
            },
            async onRefreshCallback() {
                /* this.$store.dispatch('GetSelectedProductList').then(response => {
                     setTimeout(() => {
                         this.cartList = response.Data;
                         this.computedTotalFee();
                         this.selectedAll = false;
                         this.$refs.cartLoadmore.onTopLoaded(this.$refs.cartLoadmore.uuid);
                     }, 500);
                 }, error => {
                     this.$refs.cartLoadmore.translate = 0;
                     this.$refs.cartLoadmore.topStatus = 'pull';
                     this.$refs.cartLoadmore.AllLoaded = false;
                     return this.$refs.cartLoadmore.LoadMoreLoading = false;
                 });*/
                this.$refs.cartLoadmore.translate = 0;
                this.$refs.cartLoadmore.topStatus = 'pull';
                this.$refs.cartLoadmore.AllLoaded = false;
                return this.$refs.cartLoadmore.LoadMoreLoading = false;
            },
            switchMethod() {
                this.switchValue = (this.switchValue ? "" : "√");
            },
            cancelTips() {
                this.tipsVis = false;
                if (this.switchValue) {
                    setLocalStorage("tipsVis", "false");
                } else {
                    setLocalStorage("tipsVis", "true");
                }
            },
            async emptyCart() {
                this.cartList = null;
                setLocalStorage("cart-count", "0");
            },
            async delCart(productId) {
                let newCartList = [];
                this.cartList.map(item => {
                    if (item.product.id!=productId){
                        newCartList.push(item);
                    };
                })
                this.cartList = newCartList;
            }
        },
        mounted: function () {
            this.initData();
            let tipsVis = getLocalStorage("tipsVis");
            this.tipsVis = (tipsVis == "false" ? false : true);
        }
    }
</script>
<style lang='scss' scoped>
</style>