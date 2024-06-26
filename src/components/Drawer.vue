<script setup>
import DraweHead from './DraweHead.vue'
import CartItemList from './CartItemList.vue'
import infoBlock from './infoBlock.vue'

const emit = defineEmits(['createOrder'])

defineProps({
  totalPrice: Number,
  totalVat: Number,
  buttonCartDisabled: Boolean
})
</script>

<template>
  <div class="fixed top-0 left-0 w-full h-full bg-black opacity-80 z-10"></div>
  <div class="fixed top-0 right-0 w-96 h-full z-20 bg-white p-8">
    <DraweHead />

    <div v-if="!totalPrice" class="flex h-full items-center">
      <infoBlock
        title="Ваша корзина пуста"
        description="Добавьте хотя бы одну пару кроссовок"
        imgUrl="/package-icon.png"
      />
    </div>

    <CartItemList v-if="totalPrice" />

    <div v-if="totalPrice" class="flex flex-col gap-4 mb-6 mt-7">
      <div class="flex gap-2">
        <span>Итого:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>{{ totalPrice }} ₽ </b>
      </div>

      <div class="flex gap-2">
        <span>Налог 5%:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>{{ totalVat }} ₽ </b>
      </div>

      <button
        @click="() => emit('createOrder')"
        :disabled="buttonCartDisabled"
        class="mt-4 bg-lime-500 w-full disabled:bg-slate-300 cursor-pointer rounded-xl py-3 text-white hover:bg-lime-600 active:bg-lime-700 transition"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>
