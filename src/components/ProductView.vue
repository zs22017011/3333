<script setup>
import { ref } from 'vue';
import ProductForm from './ProductForm.vue';

const products = ref([
  { id: 1, description: 'Producto 1', price: 100, name: "Producto 1 Description"},
  { id: 2, name: 'Producto 2', price: 150, description: "Producto 2 Description"},
  { id: 3, name: 'Producto 3', price: 200, description: "Producto 3 Description"},
]);

const addProduct = (product) => {
  products.value.push({
    id: Date.now(),
    ...product,
  });
};

const deleteProduct = (id) => {
  products.value = products.value.filter((product) => product.id !== id);
  /*Aqui se elimina visualmente, faltaria conectarlo a la base de datos o dejarlo asi*/
};
const editProduct = (id) => {
  /*Aqui vas a agregar la logica para editar los datos de la tabla productos*/
}
const showFormModal = ref(false);

const openFormModal = () => {
  showFormModal.value = true;
};

const closeFormModal = () => {
  showFormModal.value = false;
};
</script>

<template>
  <div class="container">
    <h1 class="MainTitle">Gestión de Productos</h1>

    <div class="product-list">
      <h2>Lista de Productos</h2>
      <table>
        <thead>
        <tr>
          <th>ID</th>
          <th>Nombre</th>
          <th>Precio</th>
          <th>Descripcion</th>
          <th>Acciones</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="product in products" :key="product.id">
          <td>{{ product.id }}</td>
          <td>{{ product.name }}</td>
          <td>${{ product.price.toFixed(2) }}</td>
          <td>{{ product.description }}</td>
          <td>
            <button class="delete-btn" @click="deleteProduct(product.id)">Eliminar</button>
            <button class="edit-btn" @click="editProduct(product.id)">Editar</button>
          </td>
        </tr>
        </tbody>
      </table>
      <div class="add-product">
        <button class="add-btn" @click="openFormModal">Agregar Producto</button>
      </div>
      <div v-if="showFormModal" class="modal-overlay">
        <div class="modal">
          <button class="close-btn" @click="closeFormModal">×</button>
          <ProductForm @add-product="addProduct" />
        </div>
      </div>
    </div>

  </div>
</template>

<style scoped>
.container {
  min-width: 85.5vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
}

.MainTitle {
  font-size: 2.5rem;
  font-weight: bold;
  text-transform: uppercase;
  background: linear-gradient(90deg, #42b983, #57799c);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 2rem;
}

.product-list {
  width: 100%;
  max-width: 600px;
  margin-bottom: 2rem;
}

.product-list table {
  width: 100%;
  border-collapse: collapse;
}

.product-list th,
.product-list td {
  border: 1px solid #ddd;
  padding: 0.75rem;
  text-align: left;
}

.product-list th {
  background-color: #f4f4f4;
}

.delete-btn {
  padding: 0.5rem 1rem;
  background: #ff4d4d;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.delete-btn:hover {
  background: #d93636;
}

.edit-btn {
  padding: 0.5rem 1rem;
  background: #57799c;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.edit-btn:hover {
  background: #2c3e50;
}
.add-product {
  display: flex;
  flex-direction: row-reverse;
  padding: 1rem;
}

.add-btn {
  padding: 0.5rem 1rem;
  background: #42b983;
  color: #fff;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

.add-btn:hover {
  background: #36a273;
}


.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal {
  background: #fff;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
  position: relative;
  width: 400px;
}

.close-btn {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #333;
}

.close-btn:hover {
  color: #d93636;
}
</style>