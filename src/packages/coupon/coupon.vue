<template>
  <div
    :class="['nut-coupon', `nut-coupon-${type}`, image == true ? 'nut-coupon-image' : '', `nut-coupon-${['get', 'use', 'ban'][state]}`]"
    v-if="item"
    @click="clickHandler"
  >
    <div class="nut-coupon-info">
      <div v-if="image == true" class="nut-coupon-imgbox">
        <img class="nut-coupon-img" :src="item.extension.u_img | jfs" />
      </div>
      <div class="nut-coupon-desc">
        <template v-if="type != '1'">
          <template v-if="typeof +item.extension.u_tit == 'number' && !isNaN(+item.extension.u_tit)">
            <div class="nut-coupon-discount">
              <span class="rmb">&yen;</span>
              {{ item.extension.u_tit }}
            </div>
          </template>
          <template v-else>
            <div class="nut-coupon-discount">
              {{ item.extension.u_tit }}
            </div>
          </template>
        </template>
        <div class="nut-coupon-quota">{{ item.extension.u_line1 }}</div>
        <!-- <div class="nut-coupon-limitStr">{{item.extension.u_line2}}</div> -->
      </div>
    </div>
    <div class="nut-coupon-limitStr">{{ item.extension.u_line2 }}</div>
    <div class="nut-coupon-btn">
      <div v-if="state == 0">立即领取</div>
      <div v-else-if="state == 1">去使用<i class="icon-arrow"></i></div>
      <div v-else-if="state == 2">已抢光</div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'nut-coupon',
  props: {
    item: {
      type: Object,
      default: null
    },
    type: {
      type: [String, Number],
      default: '1'
    },
    image: {
      type: [Boolean, String],
      default: false
    }
  },
  data() {
    return {
      state: null
    };
  },
  components: {},
  filters: {
    jfs(value) {
      if (/^jfs/.test(value)) {
        return `//m.360buyimg.com/babel/s250x250_${value}`;
      }
      return value;
    }
  },
  created() {
    // 判断券的类型
    switch (this.type) {
      case 1:
        this.setNormalCoupon();
        break;
      case 2:
        this.setNormalCoupon();
        break;
    }
  },
  mounted() {
    // console.log('item', this.item)
  },
  methods: {
    setNormalCoupon() {
      let cpnResultCode, soldOut;
      // 处理跨品类拉新券的字段过滤
      let ext = this.item.extension;
      let { couponStyle, couponType, subSku } = ext;
      ext.u_img = subSku && subSku[0] ? subSku[0].img : this.item.pictureUrl ? this.item.pictureUrl : '';
      ext.u_tit = this.cleanZero(ext.disCount);
      ext.u_line1 = this.cleanZero(ext.quota);
      ext.u_line2 = this.item.desc ? this.item.desc : ext.limitStr;
      // 金额、门槛设置
      // 京贴
      if (couponStyle == 28) {
        ext.u_line1 = `每满${this.cleanZero(ext.quota)}减${this.cleanZero(ext.disCount)}`;
      } else {
        // 折扣券
        if (couponStyle == 3) {
          if (+ext.quota) {
            ext.u_tit = `${Math.round((1 - ext.disCount / ext.quota) * 100) / 10}折`;
          }
          ext.u_line1 = +ext.quota ? `满${this.cleanZero(ext.quota)}元可用` : '无门槛';
        }
        // 满减、立减券
        if (couponType == 0 || couponType == 1) {
          ext.u_line1 = +ext.quota ? `满${this.cleanZero(ext.quota)}元可用` : '无门槛';
        }
        // 物流券
        if (couponType == 10 && couponStyle == 10) {
          ext.u_line1 = +ext.quota ? `满${this.cleanZero(ext.quota)}元可用` : '无门槛';
        }
        this.$set(this.item, 'extension', ext);
      }
      cpnResultCode = this.item.extension.cpnResultCode;
      soldOut = this.item.extension.soldOut;
      // 设置券状态
      if (cpnResultCode == 14 || cpnResultCode == 15) {
        this.state = 1; // 领过
      } else if (cpnResultCode == 16 || cpnResultCode == 17 || soldOut == 1) {
        this.state = 2; // 已抢光
      } else {
        this.state = 0; // 未领取
      }
    },
    clickHandler(event) {
      this.$emit('click', event);
    },
    getText(idx, index, sIndex) {
      if (sIndex === null) {
        return null;
      }
      const tab = (this.list && this.list[idx] && this.list[idx].children[index]) || {};
      const subTit = tab.tabTitle;
      const content = (tab.content && tab.content[sIndex]) || this.defaultContent[sIndex];
      return new Set([{ subTit, content }]);
    },
    cleanZero(value) {
      value = value;
      let res = /\.0+$/.exec(value);
      if (res) {
        return value.slice(0, res.index);
      }
      return value;
    }
  }
};
</script>
