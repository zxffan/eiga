<template>
  <view class="pay-wrap container">
    <view class="cover">
      <image class="image" src="~_images/poster1.png" />
    </view>

    <view class="info">
      <text class="normal text">Reald 3D, 10 dec4:35pm</text>
      <text class="normal text">Row 8, seats 5,6,7</text>
      <text class="exclaim text">Total: $ 24</text>
    </view>

    <view class="promocode">
      <text class="text">Use promocode?</text> <ESwitch v-model="usePromo" />
    </view>

    <view class="bankcard">
      <swiper class="swiper" previousMargin="50px" nextMargin="50px">
        <swiper-item class="swiper-item"><Bankcard /></swiper-item>
        <swiper-item class="swiper-item"><Bankcard /></swiper-item>
        <swiper-item class="swiper-item"><Bankcard /></swiper-item>
      </swiper>
    </view>

    <view class="btn">
      <EButton @tap="onPayment">Traditional Payment</EButton>
    </view>
  </view>
</template>

<script lang="ts">
import ESwitch from "../../components/Switch.vue";
import Bankcard from "../../components/Bankcard.vue";

import { ref } from "vue";
import { switchTab } from "@tarojs/taro";

export default {
  name: "Pay",

  components: { ESwitch, Bankcard },

  setup() {
    const usePromo = ref(false);

    const onPayment = () => {
      switchTab({ url: "../ticket/ticket" });
    };
    return { usePromo, onPayment };
  }
};
</script>

<style lang="scss">
.pay-wrap {
  .cover {
    margin-top: 32px;
    padding: 0 17px;
    border-radius: 10px;
    height: 160px;
    overflow: hidden;
    text-align: center;
    filter: drop-shadow(0, 1px, 3px, crimson);
    .image {
      width: 100%;
      height: 100%;
    }
  }
  .info {
    display: flex;
    flex-direction: column;
    margin-top: 10px;
    padding: 0 34px;
    .text {
      font-family: Montserrat-SemiBold;
      color: #607395;
    }
    .normal {
      margin-top: 11px;
      font-size: 16px;
    }
    .exclaim {
      margin-top: 25px;
      font-size: 22px;
    }
  }
  .promocode {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 29px;
    padding: 0 34px;
    .text {
      font-family: Montserrat-SemiBold;
      font-size: 16px;
      color: #607395;
    }
  }
  .bankcard {
    margin-top: 35px;
    padding: 0;
    .swiper {
      height: 160px;

      &-item {
        width: 280px !important;
      }
    }
  }
  .btn {
    margin-top: 47px;
    padding: 0 34px;
  }
}
</style>
