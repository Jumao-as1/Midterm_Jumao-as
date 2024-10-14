<template>
  <form @submit.prevent="submitForm" class="product-form">
    <div class="form-group">
      <label for="name">Product Name:</label>
      <input type="text" v-model="name" required />
    </div>
    <div class="form-group">
      <label for="price">Price:</label>
      <input type="number" v-model="price" required />
    </div>
    <div class="form-group">
      <label for="description">Description:</label>
      <textarea v-model="description" required></textarea>
    </div>
    <button type="submit" class="btn">Add Product</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      price: 0,
      description: ''
    };
  },
  methods: {
    submitForm() {
      const product = {
        name: this.name,
        price: this.price,
        description: this.description
      };
      this.$emit('add-product', product);
      this.name = '';
      this.price = 0;
      this.description = '';
    }
  }
};
</script>

<style scoped>
.product-form {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input, textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

input:focus, textarea:focus {
  border-color: #007bff;
}

.btn {
  background-color: #007bff;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.btn:hover {
  background-color: #0056b3;
}
</style>
