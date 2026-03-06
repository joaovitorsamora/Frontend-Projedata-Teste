<script setup>
import Products from "./views/Products.vue"
import Materials from "./views/Materials.vue"
import Optimization from "./views/Optimization.vue"
import Recipe from "./views/Recipe.vue"
</script>

<template>
  <div class="container">
    <header>
      <h1>Factory Production Optimizer</h1>
      <p>Gerenciamento e Otimização de Recursos Industriais</p>
    </header>

    <div class="dashboard-grid">
      <section class="card"><Products /></section>
      <section class="card"><Materials /></section>
      <section class="card full-width"><Recipe /></section>
      <section class="card full-width highlight"><Optimization /></section>
    </div>
  </div>
</template>

<style>
:root {
  --primary: #2c3e50;
  --accent: #42b983;
  --bg: #f4f7f6;
  --white: #ffffff;
  --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

body {
  background-color: var(--bg);
  font-family: 'Inter', sans-serif;
  color: var(--primary);
  margin: 0;
  padding: 20px;
}

.container {
  max-width: 1000px;
  margin: 0 auto;
}

header {
  text-align: center;
  margin-bottom: 40px;
}

.dashboard-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.card {
  background: var(--white);
  padding: 20px;
  border-radius: 12px;
  box-shadow: var(--shadow);
}

.full-width {
  grid-column: span 2;
}

.highlight {
  border-top: 5px solid var(--accent);
}

h2 {
  margin-top: 0;
  border-bottom: 2px solid #eee;
  padding-bottom: 10px;
  font-size: 1.2rem;
}

input, select {
  padding: 8px;
  border: 1px solid #ddd;
  border-radius: 4px;
  margin-right: 5px;
  margin-bottom: 10px;
}

button {
  background-color: var(--accent);
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 4px;
  cursor: pointer;
  transition: opacity 0.2s;
}

button:hover {
  opacity: 0.8;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  padding: 8px 0;
  border-bottom: 1px solid #eee;
}
</style>