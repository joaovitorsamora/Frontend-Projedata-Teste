<script setup>
import { ref, onMounted } from "vue"
import api from "../api/api"

const materials = ref([])
const name = ref("")
const quantity = ref("")

async function loadMaterials() {
  const response = await api.get("/raw-materials")
  materials.value = response.data
}

async function createMaterial() {
  await api.post("/raw-materials", {
    name: name.value,
    quantity: Number(quantity.value)
  })

  name.value = ""
  quantity.value = ""

  await loadMaterials()
}

onMounted(loadMaterials)
</script>

<template>
  <div>
    <h2>Raw Materials</h2>

    <input v-model="name" placeholder="Name" />
    <input v-model="quantity" placeholder="Quantity" />

    <button @click="createMaterial">Create</button>

    <ul>
      <li v-for="m in materials" :key="m.id">
        {{ m.name }} - {{ m.quantity }}
      </li>
    </ul>
  </div>
</template>