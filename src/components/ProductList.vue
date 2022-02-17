<template>
  <div>
    <div class="products">
      <div class="container">
        This is ProductList
      </div>
      <template v-for="product in products">
        <div :key="product._id" class="product">
          <!-- 其他字段 -->
          <p class="product.manufacturer">生产厂商：{{product.manufacturer.name}}</p>
          <img :src="product.image" alt="" class="product__image">
          <button @click="addToCart(product)">加入购物车</button>
        </div>
      </template>
    </div>
  </div>
</template>

<!-- style -->

<script>
export default {
  name: 'product-list',
  created() {
    if (this.products.length === 0) {
      this.$store.dispatch('allProducts')
    }
  },
  computed: {
    // ...
  },
  methods: {
    // ...
  }
}
</script>
