<script setup>
import { ref, onMounted } from "vue"
import api from "../api/api"

const products = ref([])
const name = ref("")
const code = ref("")
const price = ref("")

async function loadProducts() {
  const response = await api.get("/products")
  products.value = response.data
}

async function createProduct() {
  await api.post("/products", {
    name: name.value,
    code: code.value,
    price: Number(price.value)
  })

  name.value = ""
  code.value = ""
  price.value = ""

  await loadProducts()
}

onMounted(loadProducts)
</script>

<template>
  <div>
    <h2>📦 Produtos</h2>
    <div class="form-group">
      <input v-model="code" placeholder="Código" />
      <input v-model="name" placeholder="Nome" />
      <input v-model="price" type="number" placeholder="Preço" />
      <button @click="createProduct">Adicionar</button>
    </div>

    <ul class="list">
      <li v-for="p in products" :key="p.id">
        <strong>{{ p.code }}</strong> - {{ p.name }} 
        <span class="price-badge">R$ {{ p.price }}</span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.form-group { display: flex; flex-direction: column; }
.price-badge { 
  float: right; 
  color: #42b983; 
  font-weight: bold; 
}
</style>