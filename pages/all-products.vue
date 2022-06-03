<template>
  <div class="width-1260 px-4">
    <Breadcrumb :links="{ breadcrumb }" />

    <div class="md:grid grid-cols-12 gap-x-6">
      <!-- Shop Categries -->
      <div class="col-start-1 col-end-4">
        <ShopCategories />
      </div>

      <!-- All Products -->
      <div class="col-start-4 col-end-13">
        <h1 class="text-4xl text-primary-100">All Products</h1>

        <div>
          <!-- per page -->
          <div>
            <p>Display</p>
            <div class="relative">
              <button
                class="font-bold flex justify-between items-center w-full"
                @click="expandPerpage = !expandPerpage"
              >
                <span>Product Type</span>
                <span
                  class="transform custom-transition"
                  :class="expandPerpage ? 'rotate-0' : 'rotate-180'"
                >
                  <Icons name="chevron" />
                </span>
              </button>

              <!-- options -->

              <div
                v-if="expandPerpage"
                class="absolute top-full left-0 w-44 rounded-xl bg-gray-lighter shadow-md border"
              >
                <button
                  v-for="(item, i) in perpageOptions"
                  :key="i"
                  class="px-4 py-2 hover:bg-secondary-20 w-full"
                >
                  {{ item }} per page
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ShopCategories from '@/components/all-products/ShopCategories.vue'
import Breadcrumb from '@/components/global/Breadcrumb.vue'
import Icons from '@/components/global/Icons.vue'

export default {
  components: {
    ShopCategories,
    Breadcrumb,
    Icons,
  },

  data() {
    return {
      expandPerpage: false,
      expandSort: false,
      perpageOptions: [9, 15, 30, 40],
      sortOptions: ['Product Name'],
      breadcrumb: [
        {
          title: 'Product Slug',
          url: '#!',
        },
      ],
    }
  },
}
</script>
