<template>
  <div class="product-list">
    <h2>Product List</h2>
    <ul>
      <li v-for="(product, index) in products" :key="index" class="product-item">
        <div v-if="editingIndex === index" class="edit-form">
          <input v-model="editedProduct.name" placeholder="Edit name" />
          <input v-model="editedProduct.price" placeholder="Edit price" />
          <textarea v-model="editedProduct.description"></textarea>
          <button @click="saveEdit(index)" class="btn">Save</button>
        </div>
        <div v-else>
          <strong>{{ product.name }}</strong> - ${{ product.price }}
          <p>{{ product.description }}</p>
          <button @click="editProduct(index)" class="edit-btn">Edit</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['products'],
  data() {
    return {
      editingIndex: null,
      editedProduct: {}
    };
  },
  methods: {
    editProduct(index) {
      this.editingIndex = index;
      this.editedProduct = { ...this.products[index] };
    },
    saveEdit(index) {
      this.$emit('edit-product', { index, product: this.editedProduct });
      this.editingIndex = null;
    }
  }
};
</script>

<style scoped>
.product-list {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.product-item {
  border-bottom: 1px solid #ddd;
  padding: 10px 0;
}

.edit-form {
  margin-bottom: 10px;
}

.edit-btn {
  background-color: #007bff;
  color: white;
  padding: 5px 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.edit-btn:hover {
  background-color: #0056b3;
}
</style>
