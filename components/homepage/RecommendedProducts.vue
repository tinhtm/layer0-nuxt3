<template>
  <section class="pt-8 lg:pt-5 px-4 xl:px-0 pb-12">
    <h2 class="text-xl font-bold uppercase text-[#333]">RECOMMENDED FOR YOU</h2>

    <div
      class="mt-8 md:grid grid-cols-2 lg:grid-cols-5 gap-4 space-y-6 md:space-y-0"
    >
      <ProductCard
        v-for="(item, i) in data"
        :key="i"
        :data="item"
        :add-to-cart-btn="false"
      />
    </div>
  </section>
</template>

<script>
import ProductCard from '../ProductCard.vue'

export default {
  components: {
    ProductCard,
  },

  props: {
    data: {
      type: Array,
      default: () => [],
    },
  },

  data() {
    return {}
  },
}
</script>
