<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/catalog">Catalog</router-link> |
    <router-link to="/cart">Cart</router-link>
  </nav>
  <router-view />
</template>

<script setup lang="ts">
import { useProductStore } from './store/catalogStore';

const catalogStore = useProductStore()
catalogStore.setProducts()

</script>
