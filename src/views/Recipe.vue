<script setup>
import { ref, onMounted } from "vue"
import api from "../api/api"

const products = ref([])
const materials = ref([])
const selectedProduct = ref("")
const selectedMaterial = ref("")
const quantityRequired = ref("")


async function loadData() {
  try {
    const [resProducts, resMaterials] = await Promise.all([
      api.get("/products"),
      api.get("/raw-materials")
    ])
    products.value = resProducts.data
    materials.value = resMaterials.data
  } catch (error) {
    console.error("Erro ao carregar dados para o vínculo:", error)
  }
}

async function linkMaterial() {
  if (!selectedProduct.value || !selectedMaterial.value || !quantityRequired.value) {
    alert("Preencha todos os campos!")
    return
  }

  try {
   await api.post("/product-materials", {
      product: { id: selectedProduct.value },
      material: { id: selectedMaterial.value },
      quantityRequired: Number(quantityRequired.value)
    })

    alert("Vínculo criado com sucesso!")
    quantityRequired.value = ""
  } catch (error) {
    console.error("Erro ao vincular:", error)
  }
}

onMounted(loadData)
</script>

<template>
  <div>
    <h2>Vincular Matéria-Prima ao Produto (Receita)</h2>
    
    <div style="display: flex; gap: 10px; margin-bottom: 20px;">
      <select v-model="selectedProduct">
        <option value="" disabled>Selecione o Produto</option>
        <option v-for="p in products" :key="p.id" :value="p.id">
          {{ p.name }}
        </option>
      </select>

      <select v-model="selectedMaterial">
        <option value="" disabled>Selecione o Material</option>
        <option v-for="m in materials" :key="m.id" :value="m.id">
          {{ m.name }}
        </option>
      </select>

      <input v-model="quantityRequired" type="number" placeholder="Qtd Necessária" />

      <button @click="linkMaterial">Vincular</button>
    </div>
  </div>
</template>