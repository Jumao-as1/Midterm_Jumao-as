<template>
  <div class="products-view">
    <h2>Product Management</h2>
    <ProductForm @add-product="addProduct" />
    <ProductList :products="products" @edit-product="editProduct" />
  </div>
</template>

<script>
import ProductForm from '@/components/ProductForm.vue';
import ProductList from '@/components/ProductList.vue';

export default {
  components: {
    ProductForm,
    ProductList
  },
  data() {
    return {
      products: []
    };
  },
  methods: {
    addProduct(product) {
      this.products.push(product);
    },
    editProduct({ index, product }) {
      this.$set(this.products, index, product);
    }
  }
};
</script>

<style scoped>
.products-view {
  max-width: 800px;
  margin: auto;
  padding: 20px;
}

h2 {
  text-align: center;
  margin-bottom: 20px;
}
</style>
