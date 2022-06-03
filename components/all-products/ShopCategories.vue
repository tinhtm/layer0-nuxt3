<template>
  <section>
    <button
      class="text-gray-darkest font-bold py-1 px-2.5 bg-gray-lighter border border-gray-base rounded-r-sm md:hidden"
      @click="showMobileProductTypes = true"
    >
      Shop By
    </button>

    <!-- CATEGORIES -->
    <div class="bg-[#0132530d] p-4 rounded-sm mt-8 md:mt-0">
      <h3 class="font-bold">SHOP CATEGORIES</h3>

      <div class="pt-3 space-y-4 px-2">
        <nuxt-link
          v-for="(item, i) in categories"
          :key="i"
          :href="item.url"
          class="flex justify-start items-center text-sm font-bold text-primary-100"
        >
          <span>{{ item.name }}</span>
          <span
            v-if="item.totalItem"
            class="text-secondary-100 font-normal px-1"
            >({{ item.totalItem }})</span
          >
          <span
            v-if="item.tag"
            class="bg-secondary-a-100 text-white uppercase px-1.5 py-0.5 text-[.625rem] transform translate-x-1 rounded-sm h-5 flex justify-center items-center"
            >{{ item.tag }}</span
          >
        </nuxt-link>
      </div>
    </div>

    <!-- selected types -->
    <div class="text-sm mt-6">
      <h4 v-if="selectedTypes.length > 0" class="font-bold">Now shopping by</h4>

      <h4 v-else class="font-bold">Shopping Options</h4>

      <div class="space-y-2 mt-6">
        <div
          v-for="(item, i) in selectedTypes"
          :key="i"
          class="flex justify-start items-center space-x-2"
        >
          <button class="-mt-1" @click="removeSelectedType(item)">
            <Icons name="cross" class-list="h-3 text-gray-base removeTypebtn" />
          </button>

          <span>
            <span class="font-bold">Products Type:</span>
            <span>{{ item }}</span>
          </span>
        </div>

        <button
          v-if="selectedTypes.length > 0"
          class="mt-6 text-secondary-100"
          @click="selectedTypes = []"
        >
          Clear All
        </button>
      </div>
    </div>

    <!-- Product Types mobile -->

    <div
      v-if="showMobileProductTypes"
      class="md:hidden fixed top-0 left-0 w-screen h-screen bg-white z-50"
    >
      <div class="p-4 flex justify-between items-center border-b">
        <h3 class="font-bold">Shopping Options</h3>

        <button class="p-2" @click="showMobileProductTypes = false">
          <Icons name="cross" />
        </button>
      </div>

      <SelectProductType
        :types="types"
        @handle-type-select="handleTypeSelect"
      />
    </div>

    <!-- desktop product types -->
    <div class="hidden md:block">
      <SelectProductType
        :types="types"
        @handle-type-select="handleTypeSelect"
      />
    </div>
  </section>
</template>

<script>
import SelectProductType from './SelectProductType.vue'
import Icons from '@/components/global/Icons.vue'

export default {
  components: {
    Icons,
    SelectProductType,
  },

  data() {
    return {
      showMobileProductTypes: false,
      selectedTypes: [],
      categories: [
        {
          name: 'All Products',
          url: '#!',
          totalItem: 76,
          tag: '',
        },
        {
          name: 'Supplements',
          url: '#!',
          totalItem: 47,
          tag: '',
        },
        {
          name: 'Powders',
          url: '#!',
          totalItem: 15,
          tag: '',
        },
        {
          name: 'Bundles',
          url: '#!',
          totalItem: 15,
          tag: '',
        },
        {
          name: 'Books',
          url: '#!',
          totalItem: 5,
          tag: '',
        },
        {
          name: 'Digital Programs',
          url: '#!',
          totalItem: 4,
          tag: '',
        },
        {
          name: 'Immune',
          url: '#!',
          totalItem: 5,
          tag: '',
        },
        {
          name: 'Beauty',
          url: '#!',
          totalItem: 8,
          tag: 'New',
        },
        {
          name: 'Deals',
          url: '#!',
          totalItem: 8,
          tag: 'Hot',
        },
      ],
      types: [
        {
          name: 'Powders',
          url: '#!',
          totalItem: 15,
          tag: '',
        },
        {
          name: 'Liquid',
          url: '#!',
          totalItem: 15,
          tag: '',
        },
        {
          name: 'Capsules',
          url: '#!',
          totalItem: 5,
          tag: '',
        },
        {
          name: 'Tablets',
          url: '#!',
          totalItem: 4,
          tag: '',
        },
        {
          name: 'Tea',
          url: '#!',
          totalItem: 5,
          tag: '',
        },
        {
          name: 'Physical product',
          url: '#!',
          totalItem: 8,
          tag: 'New',
        },
      ],
    }
  },

  methods: {
    handleTypeSelect(val) {
      this.selectedTypes = [...val]
    },

    removeSelectedType(val) {
      this.selectedTypes.splice(
        this.selectedTypes.indexOf(this.selectedTypes.find((el) => el === val)),
        1
      )

      this.selectedTypes = [...this.selectedTypes]
    },
  },
}
</script>

<style>
.removeTypebtn:hover .removeTypebtn ~ span {
  @apply opacity-50;
}
</style>
