<template>
  <section
    class="flex justify-center md:justify-start items-center space-x-4 md:space-x-6 py-6"
  >
    <button
      class="text-sm px-0.5 md:px-6 py-2 rounded text-white bg-secondary-100 font-bold flex justify-center items-center"
    >
      <Icons name="chevron-left" class-list="h-4 w-4" />
      <span class="hidden md:inline">Prev</span>
    </button>

    <button class="text-sm" :class="currentPage === 1 && 'font-bold'">1</button>
    <button class="text-sm" :class="currentPage === 2 && 'font-bold'">2</button>
    <button class="text-sm" :class="currentPage === 3 && 'font-bold'">3</button>
    <button class="text-sm" :class="currentPage === 4 && 'font-bold'">4</button>

    <button
      class="text-sm px-0.5 md:px-6 py-2 rounded text-white bg-secondary-100 font-bold flex justify-center items-center"
    >
      <span class="hidden md:inline">Next</span>
      <Icons name="chevron-right" class-list="h-4 w-4" />
    </button>
  </section>
</template>

<script>
import Icons from '@/components/global/Icons.vue'

export default {
  components: {
    Icons,
  },

  data() {
    return {
      currentPage: 1,
    }
  },
}
</script>
