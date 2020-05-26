<template>
    <div class="order">
        <van-tabs v-model="active" @change="handChange">
             <van-tab title="全部"></van-tab>
            <van-tab title="待付款"></van-tab>
            <van-tab title="待发货"></van-tab>
            <van-tab title="待收货"></van-tab>
            <van-tab title="评价"></van-tab>
            <van-tab title="退款"></van-tab>
        </van-tabs>
        <div class="list">
            <div class="list-title">
                <span class="name">优选专区</span>
                <span class="icon"><van-icon name="arrow" color="#666" /></span>
                <span class="state">带付款</span>
            </div>
            <div class="cont" >
                <img :src="item.pMainPic" alt />
                <div class="info">
                    <div class="title">{{item.pName}}</div>
                    <div class="desc">{{item.desc}}</div>
                    <div class="pro-price">
                    <span class="ori-price">￥{{item.pPrice1}}</span>
                    <span class="price">￥{{item.pPrice3}}</span>
                    <span class="num">x 1</span>
                    </div>
                </div>
            </div>
            <div class="wrapper">
                共1件商品&nbsp;&nbsp;合计：<span>￥ 180.00</span> (含运费￥0.00)
            </div>
            <div class="foot">
                <div class="btn">去付款</div>
            </div>
        </div>
        
    </div>
</template>

<script>
import { Tab, Tabs, Icon } from 'vant';
export default {
    components: {
        [Tab.name]: Tab,
        [Tabs.name]: Tabs,
        [Icon.name]: Icon
    },
    data() {
        return{
            active: 1,
            oStatus: 0,
            item: {

            }
        }
    },
    methods: {
        handChange(name,title) {
            // console.log(name,title)
            if(name === 0) {
                this.oStatus = -1
            }else if(name === 1) {
                this.oStatus = -2
            }else{
                this.oStatus = Number(name) - 2
            }
            // this.getMyOrder()
        },
    }
}
</script>

<style lang="less" scoped>
@s: 0.0133rem;
.order{
    .list{
        margin-top: 20*@s;
        background: #fff;
        padding: 0 30*@s;
        .list-title{
            display: flex;
            align-items: center;
            height: 88*@s;
            color: #666;
            span{
                color: #666;
                margin-left: 20*@s;
            }
            .icon{
                flex: 1;
                padding-top: 8*@s;
                margin-left: 35*@s;
            }
            .state{
                color: #ED0C17;
            }
        }
        .cont{
            padding-top: 18*@s;
            // padding: 30 * @s;
            display: flex;
            align-items: center;
            img {
                width: 160 * @s;
                height: 160 * @s;
            }
            .info {
                flex: 1;
                margin-left: 30 * @s;
                .desc {
                    color: #808080;
                    margin-top: 10 * @s;
                    font-size: 24 * @s;
                    margin-bottom: 10 * @s;
                }
                .ori-price {
                    font-size: 28 * @s;
                    margin-right: 10 * @s;
                    text-decoration: line-through;
                }
                .price {
                    color: #ed0c17;
                    font-size: 32 * @s;
                    font-weight: bold;
                }
                .pro-price{
                    display: flex;
                    align-items: center;
                    .price{
                        flex: 1
                    }
                    .num{
                        font-size: 22*@s;
                        color: #999;
                    }
                }
            }
        }
        .wrapper{
            text-align: right;
            line-height: 87*@s;
            border-bottom: 1px solid #f2f2f2;
            font-size: 24*@s;
            color: #666;
            span{
                font-size: 32*@s;
                color: #000;
            }
            .dis-price{
                color: #ED0C17;
            }
        }
        .foot{
            text-align: right;
            line-height: 88*@s;
            .btn{
                font-size: 24*@s;
                display: inline-block;
                width: 160*@s;
                line-height: 54*@s;
                color: #D11529;
                border: 1px solid #D11529;
                border-radius: 27*@s;
                text-align: center;
                margin-left: 20*@s;
            }
            .active{
                color: #ED0C17;
                border: 1px solid #ED0C17;
            }
        }
    }
    .tip{
        line-height: 88*@s;
        color: #999;
        text-align: center;
    }
}
</style>