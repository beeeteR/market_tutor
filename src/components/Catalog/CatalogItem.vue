<template>
  <div class="catalog-item">
    <div class="catalog-item__img">
      <img :src="data.image" alt="" width="100" height="100">
    </div>
    <div class="catalog-item__title">{{ data.title }}</div>
    <div class="catalog-item__price">{{ data.price }}</div>
    <div class="catalog-item__category">{{ data.category }}</div>
    <button class="catalog-item__btn add-to-cart" @click="cartStore.addProduct(data)"
      v-if="router.currentRoute.value.path.indexOf('cart') == -1">Добавить в корзину</button>
    <div class="cart-item__btns" v-if="router.currentRoute.value.path.indexOf('cart') != -1">
      <button class="catalog-item__btn incr" @click="cartStore.changeCountProduct('incr', props.data.article)">+</button>
      <span class="cart-item count">{{ data.count }}</span>
      <button class="catalog-item__btn desc" @click="cartStore.changeCountProduct('desc', props.data.article)">-</button>
      <button class="catalog-item__btn remove-from-cart" @click="cartStore.removeProductFromCart(data.article)">Удалить из
        корзины</button>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { useCartStore } from '@/store/cartStore';
import { IProduct, IProductCart } from '../../store/types';
import { defineProps, PropType } from 'vue'
import router from '@/router';


const props = defineProps({
  data: {
    type: Object as PropType<IProduct & IProductCart>,
    required: true
  }
})

const cartStore = useCartStore()

</script>
