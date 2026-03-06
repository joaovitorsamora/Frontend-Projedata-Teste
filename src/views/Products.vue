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
    <h2>Products</h2>

    <input v-model="code" placeholder="Code" />
    <input v-model="name" placeholder="Name" />
    <input v-model="price" placeholder="Price" />

    <button @click="createProduct">Create</button>

    <ul>
      <li v-for="p in products" :key="p.id">
        {{ p.name }} - {{ p.price }}
      </li>
    </ul>
  </div>
</template>