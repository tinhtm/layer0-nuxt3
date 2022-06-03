<template>
  <section class="h-screen w-screen bg-gray-900 bg-opacity-50">
    <div
      class="px-4 pt-[60%] md:pt-[40%] xl:pt-[18%] md:px-16 max-w-[45rem] lg:px-4 mx-auto"
    >
      <!-- Click outside -->
      <div
        class="flex justify-start items-center space-x-1.5 border w-auto py-3 px-3 md:pl-5 bg-white rounded-[36px]"
      >
        <Icons name="search" />

        <input
          type="text"
          placeholder="Search for Dr. Berg health products"
          :value="searchText"
          class="text-gray-darker h-full w-full bg-white py-1"
        />

        <button
          v-if="searchText"
          class="p-2 rounded-full bg-gray-light"
          @click="searchText = ''"
        >
          <Icons name="cross" height="10" width="10" />
        </button>

        <button
          class="px-2.5 pb-1 pt-2 rounded-full bg-secondary-100 text-white flex justify-center items-center space-x-1 text-xs font-semibold"
        >
          <Icons name="search-box-arrow" width="6" />
          <span class="-mt-1">Search</span>
        </button>
      </div>
    </div>
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
      searchText: '',
      selectedRating: null,
      ratings: [1, 2, 3, 4, 5],
    }
  },

  methods: {
    onChecked(e) {
      this.selectedRating = e.target.value
    },
    dispatch(name, data) {
      this.$emit(name, data)
    },
  },
}
</script>
