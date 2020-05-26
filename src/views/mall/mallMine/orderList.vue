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
    </div>
</template>

<script>
import { Tab, Tabs } from 'vant';
export default {
    components: {
        [Tab.name]: Tab,
        [Tabs.name]: Tabs
    },
    data() {
        return{
            active: 1,
            oStatus: 0
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

<style>

</style>