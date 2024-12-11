<script setup>
import { ref, defineEmits } from 'vue';

const productName = ref('');
const productPrice = ref('');
const productDescription = ref('');

const emit = defineEmits(['add-product']);

const handleSubmit = () => {
  if (productName.value && productPrice.value && productDescription.value) {
    emit('add-product', {
      name: productName.value,
      price: parseFloat(productPrice.value),
      productDescription: productDescription.value
    });

    productName.value = '';
    productPrice.value = '';
    productDescription.value = '';
  } else {
    alert('Por favor, completa todos los campos.');
  }
};
</script>

<template>
  <div class="product-form">
    <h2>Agregar Producto</h2>
    <form @submit.prevent="handleSubmit">
      <label for="name">Nombre del Producto</label>
      <input
          type="text"
          id="name"
          v-model="productName"
          placeholder="Nombre del producto"
          required
      />

      <label for="price">Precio</label>
      <input
          type="number"
          id="price"
          v-model="productPrice"
          placeholder="Precio"
          min="0"
          required
      />
      <label for="description">Descripción</label>
      <input
          type="text"
          id="description"
          v-model="productDescription"
          placeholder="Descripción del producto"
          required
      />

      <button type="submit" class="add-btn">Agregar Producto</button>
    </form>
  </div>
</template>

<style scoped>
.product-form {
  width: 100%;
  max-width: 400px;
  padding: 2rem;
  background: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.product-form label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: bold;
}

.product-form input {
  width: 100%;
  padding: 0.75rem;
  margin-bottom: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.product-form input:focus {
  border-color: #42b983;
  outline: none;
  box-shadow: 0 0 4px rgba(66, 185, 131, 0.6);
}

.add-btn {
  width: 100%;
  padding: 0.75rem;
  background: #42b983;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.add-btn:hover {
  background: #36a273;
}
</style>