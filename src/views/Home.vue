<template>
  <div class="home">
    <ProductDescriptionDrawer 
      :product='product'
      :active='active.product_drawer'
    />

    <div class='product-container'>
      <ProductSummaryCard
      v-for='product in items'
      :key='product.id'
      :product='product'
      v-on:view-product='viewProduct($event)' 
      />
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import items from '../data/items.js'
import ProductSummaryCard from '../components/products/ProductSummaryCard.vue'
import ProductDescriptionDrawer from '../components/products/ProductDescriptionDrawer.vue'

export default {
  name: 'Home',
  components: {
    ProductSummaryCard, ProductDescriptionDrawer
  },
  data () {
    return {
      items: items,
      product: null,
      active: {
        product_drawer: false
      }

    }
  },
  methods: {
    viewProduct(product) {
      this.product = product
      console.log(this.product)

    }
  }
}
</script>
<style>
  .product-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
</style>