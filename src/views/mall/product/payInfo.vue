<template>
  <div>
    <div class="sum">
      <div class="item">
        <div class="name">支付详情</div>
      </div>
      <!-- <div class="item">
                <div class="name">商品总格：</div>
                <div class="value" >￥{{allTotal}}</div>
            </div> -->
      <div class="item">
        <div class="name">已支付：</div>
        <div class="value">￥{{ paidSum }}</div>
      </div>
      <div class="item">
        <div class="name">待支付：</div>
        <div class="value">￥{{ needPaySum }}</div>
      </div>
    </div>
    <div style="margintop: 0.4rem">
      <van-field
        v-model="value"
        label="支付"
        placeholder="请输入支付金额"
        type="number"
      />
    </div>
    <div class="btn" @click="pay">支付</div>
  </div>
</template>

<script>
import { Field } from 'vant';
export default {
  components: {
    [Field.name]: Field
  },
  data () {
    return {
      pbCode: '',
      allTotal: '',
      paidSum: '',
      needPaySum: '',
      total: '',
      value: ''
    }
  },
  methods: {
    getPayInfo () {
      this.$api.mall.prdBillPartPayInfo({ pbCode: this.pbCode }).then(res => {
        console.log(res)
        if (res.resultCode === 1) {
          this.paidSum = res.data.paidSum
          this.needPaySum = res.data.needPaySum
        }
      })
    },
    pay () {
      let parms = {
        priceType: 0,
        pbCode: this.pbCode,
        paySum: this.value
      }
      this.$api.mall.prdBillpay(parms).then(res => {
        if (res.resultCode === 1) {
          window.location.href = res.msg
        }
      })
    }
  },
  mounted () {
    this.pbCode = this.$route.query.pbCode
    this.getPayInfo()
  }

}
</script>

<style lang="less" scoped>
@s: 0.0133rem;
.sum {
  padding: 40 * @s;
  font-size: 24 * @s;
  background: #fff;
  // margin-top: 30*@s;
  .item {
    display: flex;
    align-items: center;
    font-weight: bold;
    height: 80 * @s;
    // padding-top: 35*@s;
    .name {
      flex: 1;
    }
    input {
      width: 490 * @s;
      flex-shrink: 0;
    }
    span {
      font-weight: bold;
      color: #ff0101;
    }
    .right {
      margin-left: 15 * @s;
      color: #333;
    }
    &:first-child {
      border-bottom: 1px solid #c8c8c8;
      font-size: 26 * @s;
    }
  }
  .total {
    border-top: 1px solid #c8c8c8;
    padding-top: 30 * @s;
  }
}
.btn {
  font-size: 30 * @s;
  width: 500 * @s;
  line-height: 80 * @s;
  border-radius: 40 * @s;
  background: #7eb4da;
  color: #fff;
  text-align: center;
  margin: 50 * @s auto;
  margin-top: 200 * @s;
}
</style>