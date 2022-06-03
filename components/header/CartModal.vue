<template>
  <section class="p-4">
    <div v-if="data && data.length > 0">
      <h4 class="text-gray-darkest font-bold text-lg">Your cart</h4>

      <!-- Cart Items -->
      <div class="mt-4 space-y-4 border-b pb-4">
        <div
          v-for="(item, i) in data"
          :key="i"
          class="flex justify-between items-center space-x-2"
        >
          <div class="w-[15%]">
            <img
              :src="item.image || ''"
              alt=""
              class="max-h-12 w-full object-contain object-center"
            />
          </div>

          <p class="w-[70%]">{{ item.qty || 1 }}x {{ item.name || '' }}</p>
          <span class="w-[15%] text-right font-bold"
            >${{ item.price.toFixed(2) }}</span
          >
        </div>
      </div>

      <!-- total -->
      <div class="mt-4">
        <div class="flex justify-between items-center">
          <span>
            <span class="font-bold">Total:</span>
            <span>{{ data.length }} products</span>
          </span>

          <span class="text-right font-bold">{{ totalPrice.toFixed(2) }}</span>
        </div>

        <nuxt-link
          href="/mgicheckout/cart"
          class="mt-4 inline-block bg-secondary-100 px-4 py-2 rounded text-white font-semibold text-sm"
          >View cart</nuxt-link
        >
      </div>
    </div>

    <div v-else class="py-6">
      <p class="text-center">You have no items in your shopping cart</p>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      data: [
        {
          name: 'Hair Formula',
          price: 99,
          qty: 1,
          image: '/images/product/product-1.jpg',
        },
        {
          name: 'Scalp and Hair Follicle Serum',
          price: 99,
          qty: 1,
          image: '/images/product/product-2.jpg',
        },
        {
          name: 'Clean Lather Shampoo and Clean Shine Conditioner Bundle',
          price: 99,
          qty: 1,
          image: '/images/product/product-3.jpg',
        },
      ],
      totalPrice: 0,
    }
  },

  mounted() {
    this.getTotal()
  },

  methods: {
    getTotal() {
      let total = 0
      this.data.forEach((item) => {
        total += item.price * item.qty
      })

      this.totalPrice = total
    },
  },
}
</script>
