<template>
  <!-- Click outside -->
  <div class="h-screen w-full bg-white max-w-[30rem]">
    <!-- search and cross button -->
    <div class="grid grid-cols-5 px-5 pt-6 pb-8">
      <button
        class="col-start-1 col-end-5 flex justify-start items-center space-x-1.5 py-3 px-6 bg-gray-lighter hover:bg-gray-light rounded-3xl sm:hidden"
        @click="showSearch"
      >
        <Icons name="search" />
        <span class="text-gray-darker truncate"
          >Search for Dr. Berg health products</span
        >
      </button>

      <button
        class="col-start-6 px-2 sm:col-start-1 sm:col-end-2 lg:ml-8"
        @click="closeMenu"
      >
        <Icons name="cross" />
      </button>

      <nuxt-link
        to="/"
        class="mr-16 sm:col-start-2 sm:col-end-6 hidden sm:block"
      >
        <img src="/images/logo-small.svg" alt="" class="h-16" />
      </nuxt-link>
    </div>

    <!-- nav Items -->
    <div class="lg:grid grid-cols-5 px-5">
      <div
        class="flex flex-col justify-start items-start space-y-4 pt-4 lg:col-start-2 lg:col-end-6 lg:space-y-6"
      >
        <nuxt-link
          v-for="(item, i) in navList"
          :key="i"
          :href="item.url"
          class="flex justify-center items-center text-xl font-bold text-primary-100"
        >
          <span>{{ item.name }}</span>

          <span v-if="item.totalItem" class="lg:hidden"
            >({{ item.totalItem }})</span
          >

          <span
            v-if="item.tag"
            class="bg-secondary-a-100 text-white px-1 py-0.5 text-[.625rem] transform -translate-y-1 translate-x-1 rounded-lg h-5 flex justify-center items-center"
            >{{ item.tag }}</span
          >
        </nuxt-link>
      </div>
    </div>

    <!-- other Dr. Berg associated apps  -->
    <div class="sm:hidden mt-6 px-5 flex flex-col justify-start">
      <a href="https://drberg.com" target="_blank" class="text-gray-darker"
        >drberg.com</a
      >
      <a href="courses.drberg.com" class="text-gray-darker mt-2"
        >courses.drberg.com</a
      >
    </div>
  </div>
</template>

<script>
import Icons from '@/components/global/Icons.vue'
// import { clickOutside } from '../js/clickOutside';

export default {
  components: {
    Icons,
  },

  data() {
    return {
      navList: [
        {
          name: 'All Products',
          url: '/all-products',
          totalItem: 76,
          tag: '',
        },
        {
          name: 'Supplements',
          url: '/supplements',
          totalItem: 47,
          tag: '',
        },
        {
          name: 'Powders',
          url: '/powders',
          totalItem: 15,
          tag: '',
        },
        {
          name: 'Bundles',
          url: '/bundles',
          totalItem: 15,
          tag: '',
        },
        {
          name: 'Books',
          url: '/books',
          totalItem: 5,
          tag: '',
        },
        {
          name: 'Digital Programs',
          url: '/digital-programs',
          totalItem: 4,
          tag: '',
        },
        {
          name: 'Immune',
          url: '/immune',
          totalItem: 5,
          tag: '',
        },
        {
          name: 'Beauty',
          url: '/beauty',
          totalItem: 8,
          tag: 'New',
        },
        {
          name: 'Deals',
          url: '/deals',
          totalItem: null,
          tag: 'Hot',
        },
      ],
    }
  },

  methods: {
    closeMenu() {
      this.$emit('close')
    },

    showSearch() {
      this.closeMenu()
      this.$emit('showSearch')
    },

    handleClickOutside() {
      this.$emit('close')
    },
  },
}
</script>
