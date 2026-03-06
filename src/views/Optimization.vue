<script setup>
import { ref } from "vue"
import api from "../api/api"

const result = ref(null)

async function optimize() {
  try {
    const response = await api.get("/optimize-production")
    result.value = response.data
  } catch (error) {
    console.error("Optimization error:", error)
  }
}
</script>

<template>
  <div>
    <h2>Production Optimization</h2>

    <button @click="optimize">
      Calcular
    </button>

    <div v-if="result">
      <h3>Maximum Production</h3>

      <div v-for="(value, key) in result" :key="key">
        {{ key }} → {{ value }} units
      </div>
    </div>
  </div>
</template>