<template>
  <div class="demo-list">
    <!-- 京贴券 -->
    <h4>京贴券</h4>
    <div class="wrapper-coupon-box">
      <div class="coupon-box">
        <div class="coupon-item" v-for="(item, index) in couponList1.list" :key="index">
          <nut-coupon :item="item" :type="1" @click="handleClick()" />
        </div>
      </div>
    </div>
    <!-- 品类券无图 -->
    <h4>品类券无图</h4>
    <div class="wrapper-coupon-box">
      <div class="coupon-box">
        <div class="coupon-item" v-for="(item, index) in couponList2.list" :key="index">
          <nut-coupon :item="item" :type="2" :image="false" @click="handleClick()" />
        </div>
      </div>
    </div>
    <!-- 品类券有图 -->
    <h4>品类券无图</h4>
    <div class="wrapper-coupon-box">
      <div class="coupon-box">
        <div class="coupon-item" v-for="(item, index) in couponList3.list" :key="index">
          <nut-coupon :item="item" :type="2" :image="true" @click="handleClick()" />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      couponList1: {
        list: [
          {
            desc: '',
            extension: {
              disCount: '1.0',
              quota: '10.0',
              limitStr: '仅可购买京贴测试商品',
              soldOut: 0,
              couponStyle: 28,
              couponType: 1,
              key: 'm4a4t8ear2i8a9l5c5m0s4d2e9956535',
              roleId: '44621386',
              venderId: 0,
              subSku: [
                {
                  img: 'jfs/t1/137621/21/15770/49049/5fbe0520E043b4ce5/f8a1e0e877908389.jpg',
                  sku: 100016773618
                }
              ],
              soldOut: 0,
              cpnResultCode: 200
            }
          },
          {
            desc: '仅可购买年货节头号京贴活动商品',
            linkParam: '',
            extension: {
              disCount: '1.0',
              quota: '5.0',
              limitStr: '仅可购买京贴测试商品',
              soldOut: 0,
              couponStyle: 28,
              couponType: 1,
              key: 'm3a5t7e4r9iaa0lcc9m0sd7c0203d72f',
              roleId: '44621383',
              venderId: 0,
              subSku: [
                {
                  img: 'jfs/t1/132022/33/3322/189592/5ef9d0c4Ece6a3708/c5dc348d3f943324.jpg!q50.jpg',
                  sku: 100016773618
                }
              ],
              soldOut: 0,
              cpnResultCode: 14
            }
          },
          {
            desc: '仅可购买年货节头号京贴活动商品',
            linkParam: '',
            extension: {
              disCount: '1.0',
              quota: '5.0',
              limitStr: '仅可购买京贴测试商品',
              soldOut: 0,
              couponStyle: 28,
              couponType: 1,
              key: 'm3a5t7e4r9iaa0lcc9m0sd7c0203d72f',
              roleId: '44621383',
              venderId: 0,
              subSku: [
                {
                  img: 'jfs/t1/132022/33/3322/189592/5ef9d0c4Ece6a3708/c5dc348d3f943324.jpg!q50.jpg',
                  sku: 100016773618
                }
              ],
              soldOut: 0,
              cpnResultCode: 16
            }
          }
        ]
      },
      couponList2: {
        list: [
          {
            desc: '',
            extension: {
              disCount: '1.0',
              quota: '10.0',
              limitStr: '仅可购买京贴测试商品',
              soldOut: 0,
              couponStyle: 0,
              couponType: 1,
              key: 'm4a4t8ear2i8a9l5c5m0s4d2e9956535',
              roleId: '44621386',
              venderId: 0,
              subSku: [
                {
                  img: 'jfs/t1/137621/21/15770/49049/5fbe0520E043b4ce5/f8a1e0e877908389.jpg',
                  sku: 100016773618
                }
              ],
              soldOut: 0,
              cpnResultCode: 200
            }
          },
          {
            desc: '仅可购买年货节头号京贴活动商品',
            linkParam: '',
            extension: {
              disCount: '1.0',
              quota: '5.0',
              limitStr: '仅可购买京贴测试商品',
              soldOut: 0,
              couponStyle: 0,
              couponType: 1,
              key: 'm3a5t7e4r9iaa0lcc9m0sd7c0203d72f',
              roleId: '44621383',
              venderId: 0,
              subSku: [
                {
                  img: 'jfs/t1/132022/33/3322/189592/5ef9d0c4Ece6a3708/c5dc348d3f943324.jpg!q50.jpg',
                  sku: 100016773618
                }
              ],
              soldOut: 0,
              cpnResultCode: 14
            }
          },
          {
            desc: '仅可购买年货节头号京贴活动商品',
            linkParam: '',
            extension: {
              disCount: '1.0',
              quota: '5.0',
              limitStr: '仅可购买京贴测试商品',
              soldOut: 0,
              couponStyle: 3,
              couponType: 1,
              key: 'm3a5t7e4r9iaa0lcc9m0sd7c0203d72f',
              roleId: '44621383',
              venderId: 0,
              subSku: [
                {
                  img: 'jfs/t1/132022/33/3322/189592/5ef9d0c4Ece6a3708/c5dc348d3f943324.jpg!q50.jpg',
                  sku: 100016773618
                }
              ],
              soldOut: 0,
              cpnResultCode: 16
            }
          }
        ]
      },
      couponList3: {
        list: [
          {
            desc: '',
            extension: {
              disCount: '1.0',
              quota: '10.0',
              limitStr: '仅可购买京贴测试商品',
              soldOut: 0,
              couponStyle: 0,
              couponType: 1,
              key: 'm4a4t8ear2i8a9l5c5m0s4d2e9956535',
              roleId: '44621386',
              venderId: 0,
              subSku: [
                {
                  img: 'jfs/t1/137621/21/15770/49049/5fbe0520E043b4ce5/f8a1e0e877908389.jpg',
                  sku: 100016773618
                }
              ],
              soldOut: 0,
              cpnResultCode: 200
            }
          },
          {
            desc: '仅可购买年货节头号京贴活动商品',
            linkParam: '',
            extension: {
              disCount: '1.0',
              quota: '5.0',
              limitStr: '仅可购买京贴测试商品',
              soldOut: 0,
              couponStyle: 0,
              couponType: 1,
              key: 'm3a5t7e4r9iaa0lcc9m0sd7c0203d72f',
              roleId: '44621383',
              venderId: 0,
              subSku: [
                {
                  img: 'jfs/t1/132022/33/3322/189592/5ef9d0c4Ece6a3708/c5dc348d3f943324.jpg!q50.jpg',
                  sku: 100016773618
                }
              ],
              soldOut: 0,
              cpnResultCode: 14
            }
          },
          {
            desc: '仅可购买年货节头号京贴活动商品',
            linkParam: '',
            extension: {
              disCount: '1.0',
              quota: '5.0',
              limitStr: '仅可购买京贴测试商品',
              soldOut: 0,
              couponStyle: 3,
              couponType: 1,
              key: 'm3a5t7e4r9iaa0lcc9m0sd7c0203d72f',
              roleId: '44621383',
              venderId: 0,
              subSku: [
                {
                  img: 'jfs/t1/132022/33/3322/189592/5ef9d0c4Ece6a3708/c5dc348d3f943324.jpg!q50.jpg',
                  sku: 100016773618
                }
              ],
              soldOut: 0,
              cpnResultCode: 16
            }
          }
        ]
      }
    };
  },
  methods: {
    handleClick() {
      this.$toast.text('很抱歉，没抢到~~');
    }
  }
};
</script>

<style lang="scss" scoped>
.demo-list /deep/ p {
  padding: 0;
  margin: 0;
}
.coupon-box {
  display: flex;
  flex: 0 0 auto;
  overflow-x: auto;
  .coupon-item {
    position: relative;
    margin-right: 10px;
  }
}
</style>
