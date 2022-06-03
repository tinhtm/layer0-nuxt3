<template>
  <section
    class="bg-gray-lighter p-6 md:px-3 lg:px-6 md:flex justify-between items-center mt-5 rounded"
  >
    <div
      class="md:flex justify-start items-stretch space-y-3 md:space-y-0 md:space-x-3"
    >
      <!-- per page -->
      <div class="text-xs flex justify-start items-center space-x-1">
        <p>Display:</p>
        <!-- Vue clickoutside here -->

        <div class="relative">
          <button
            class="flex justify-between items-center space-x-5 w-full bg-secondary-10 px-4 py-2 rounded"
            @click="expandPerpage = !expandPerpage"
          >
            <span>{{ selectedPerpage }} per page</span>
            <span
              class="text-secondary-80 transform custom-transition"
              :class="expandPerpage ? 'rotate-180' : 'rotate-0'"
            >
              <Icons name="chevron" class-list="h-6 w-6" />
            </span>
          </button>

          <!-- options -->
          <div
            v-if="expandPerpage"
            class="absolute top-full left-0 w-full rounded-xl bg-secondary-10 shadow-md border overflow-hidden"
          >
            <button
              v-for="(item, i) in perpageOptions"
              :key="i"
              class="px-4 py-2 hover:bg-secondary-20 w-full"
              @click="setPerpage(item)"
            >
              {{ item }} per page
            </button>
          </div>
        </div>
      </div>

      <!-- sort -->
      <div class="flex justify-start items-stretch space-x-1">
        <div class="text-xs flex justify-start items-center space-x-1">
          <p>Sort by:</p>
          <!-- Vue clickoutside here -->
          <div class="relative">
            <button
              class="flex justify-between items-center space-x-5 w-full bg-secondary-10 px-4 py-2 rounded"
              @click="expandSort = !expandSort"
            >
              <span>{{ selectedSort }}</span>
              <span
                class="text-secondary-80 transform custom-transition"
                :class="expandSort ? 'rotate-180' : 'rotate-0'"
              >
                <Icons name="chevron" class-list="h-6 w-6" />
              </span>
            </button>

            <!-- options -->
            <div
              v-if="expandSort"
              class="absolute top-full left-0 w-full rounded-xl bg-secondary-10 shadow-md border overflow-hidden"
            >
              <button
                v-for="(item, i) in sortOptions"
                :key="i"
                class="px-4 py-2 hover:bg-secondary-20 w-full"
                @click="setSort(item)"
              >
                {{ item }}
              </button>
            </div>
          </div>
        </div>

        <!-- asc | desc -->
        <button
          class="px-2 bg-white rounded text-primary-100 flex justify-center items-center"
          @click="setAscDsc"
        >
          <span
            class="text-secondary-80 transform custom-transition inline-block focus:transform-none"
            :class="
              !ascending ? '-rotate-180 hover:rotate-0' : 'hover:-rotate-180'
            "
          >
            <Icons name="arrow-up" class-list="h-5 w-5" />
          </span>
        </button>
      </div>
    </div>

    <!-- display grid -->
    <div class="hidden md:block">
      <button
        class="p-2"
        :class="displayGrid ? 'bg-secondary-10' : 'bg-white'"
        @click="setDisplayView"
      >
        <img src="/images/all-product/icon_grid.svg" alt="" />
      </button>

      <button
        class="p-2 bg-white"
        :class="!displayGrid ? 'bg-secondary-10' : 'bg-white'"
        @click="setDisplayView"
      >
        <img src="/images/all-product/icon_list.svg" alt="" />
      </button>
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
      expandPerpage: false,
      expandSort: false,
      selectedPerpage: 40,
      selectedSort: 'Product Name',
      ascending: true,
      displayGrid: true,
      perpageOptions: [9, 15, 30, 40],
      sortOptions: ['Product Name'],
    }
  },

  methods: {
    setPerpage(perpage) {
      this.selectedPerpage = perpage
    },

    setSort(sort) {
      this.selectedSort = sort
    },

    setAscDsc() {
      this.ascending = !this.ascending
    },

    setDisplayView() {
      this.displayGrid = !this.displayGrid
      this.$emit('set-display-view')
    },
  },
}
</script>
