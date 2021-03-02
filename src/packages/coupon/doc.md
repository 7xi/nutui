# Coupon 优惠券

## 基本用法

```html
<nut-coupon :item="item" :type="1" />
```

## 京贴券

```html
<nut-coupon :item="item" :type="1" @click="handleClick()" />
```

```javascript
export default {
  data() {
    return {
      couponList1: {
        list: [
          {
            extension: {
              disCount: "1.0",
              quota: "10.0",
              limitStr: "仅可购买京贴测试商品",
              soldOut: 0,
              couponStyle: 28,
              couponType: 1,
              key: "m4a4t8ear2i8a9l5c5m0s4d2e9956535",
              roleId: "44621386",
              venderId: 0,
              soldOut: 0,
              cpnResultCode: 200
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
```

## 品类券无图

```html
<nut-coupon :item="item" :type="2" :image="false" @click="handleClick()" />
```

```javascript
export default {
  data() {
    return {
      couponList2: {
				list: [
          {
            extension: {
              disCount: "1.0",
              quota: "10.0",
              limitStr: "仅可购买京贴测试商品",
              soldOut: 0,
              couponStyle: 0,
              couponType: 1,
              key: "m4a4t8ear2i8a9l5c5m0s4d2e9956535",
              roleId: "44621386",
              venderId: 0,
              subSku: [{
                img: "jfs/t1/137621/21/15770/49049/5fbe0520E043b4ce5/f8a1e0e877908389.jpg",
                sku: 100016773618,
              }],
              soldOut: 0,
              cpnResultCode: 200,
            },
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
```

## 品类券无图

```html
<nut-coupon :item="item" :type="2" :image="true" @click="handleClick()" />
```
```javascript
export default {
  components: {},
  data() {
    return {
      couponList3: {
				list: [
          {
            extension: {
              disCount: "1.0",
              quota: "10.0",
              limitStr: "仅可购买京贴测试商品",
              soldOut: 0,
              couponStyle: 0,
              couponType: 1,
              key: "m4a4t8ear2i8a9l5c5m0s4d2e9956535",
              roleId: "44621386",
              venderId: 0,
              subSku: [{
                img: "jfs/t1/137621/21/15770/49049/5fbe0520E043b4ce5/f8a1e0e877908389.jpg",
                sku: 100016773618,
              }],
              soldOut: 0,
              cpnResultCode: 200,
            },
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
```

### Prop

| 字段              | 说明                                       | 类型    | 默认值   |
| ----------------- | ------------------------------------------ | ------- | -------- |
| item       | 优惠券数据                              | object  | -      | 
| type         | 优惠券品类类型                              | String  | 1(京贴)、2（品类券）       | 1
| Image    | 优惠券图片                | Boolean  | false     |