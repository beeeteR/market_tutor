<template>
  <catalog-list :products="cartStore.products"></catalog-list>
</template>

<script lang="ts" setup>
import { useCartStore } from "@/store/cartStore";
import CatalogList from "@/components/Catalog/CatalogList.vue";

const cartStore = useCartStore()

</script>
