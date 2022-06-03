<template>
  <header class="relative bg-white xmd:pb-0">
    <!-- top panel -->
    <div v-if="topPanelMsg" class="bg-gray-darkest py-3 px-6">
      <p class="text-white uppercase text-center">{{ topPanelMsg }}</p>
    </div>

    <div class="px-5 lg:px-8">
      <!-- header line one -->
      <div
        class="flex justify-between items-center border-b lg:border-none py-2"
      >
        <div class="flex justify-start items-center">
          <button class="header-icon-btn mr-4" @click="toggleMenu">
            <Icons name="menu" />
          </button>

          <nuxt-link to="/" class="mr-16">
            <img src="/images/logo.svg" alt="" class="hidden xl:block h-12" />
            <img src="/images/logo-small.svg" alt="" class="xl:hidden h-10" />
          </nuxt-link>

          <button
            class="hidden xmd:flex justify-start items-center space-x-1.5 w-auto 2xl:w-[30rem] py-2 px-6 bg-gray-lighter hover:bg-gray-light rounded-3xl"
            @click="toggleSearchBox"
          >
            <Icons name="search" />
            <span class="text-gray-darker"
              >Search for Dr. Berg health products</span
            >
          </button>
        </div>

        <!-- Icon Buttons -->
        <div class="flex justify-end items-center space-x-3 sxl:space-x-1">
          <!-- search -->
          <button
            class="xmd:hidden h-8 w-8 md:h-11 md:w-11 bg-none hover:bg-primary-5 rounded-full p-1 flex justify-center items-center transition duration-300 ease-in-out"
          >
            <Icons name="search" />
          </button>

          <!-- Click Outside -->
          <div class="relative">
            <button
              class="hidden h-11 w-11 bg-none hover:bg-primary-5 rounded-full p-1 sm:flex justify-center items-center transition duration-300 ease-in-out"
              @click="toggleOthersAppList"
            >
              <Icons name="nine-dots" />
            </button>

            <div
              v-if="showOthersAppList"
              class="absolute top-4 right-0 bg-white py-2 shadow mt-6 flex flex-col justify-start z-50"
            >
              <a
                href="https://drberg.com"
                target="_blank"
                class="text-gray-darker w-full py-2 px-4"
                >drberg.com</a
              >
              >
              <a
                href="https://courses.drberg.com"
                target="_blank"
                class="text-gray-darker w-full py-2 px-4"
                >courses.drberg.com</a
              >
              >
            </div>
          </div>

          <!-- info -->
          <button
            class="hidden h-11 w-11 bg-none hover:bg-primary-5 rounded-full p-1 xmd:flex justify-center items-center transition duration-300 ease-in-out"
          >
            <Icons name="info" />
          </button>

          <!-- wishlist -->
          <nuxt-link
            to="/wishlist"
            class="hidden h-11 w-11 bg-none hover:bg-primary-5 rounded-full p-1 sm:flex justify-center items-center transition duration-300 ease-in-out"
          >
            <Icons name="love-outline" />
          </nuxt-link>

          <!-- profile -->
          <!-- Click Outside -->
          <div class="relative">
            <button class="header-icon-btn" @click="toggleProfile">
              <Icons name="avatar" />
            </button>

            <div
              v-if="showProfile"
              class="absolute top-full right-0 bg-white z-50 shadow w-64 rounded p-1"
            >
              <ProfileModal />
            </div>
          </div>

          <!-- Click Outside -->
          <div use class="relative">
            <button class="header-icon-btn" @click="toggleCartModal">
              <Icons name="cart" />
            </button>

            <div
              v-if="showCartModal"
              class="absolute top-full right-0 bg-white z-50 shadow w-[22rem] rounded p-1"
            >
              <CartModal />
            </div>
          </div>
        </div>
      </div>

      <!-- header line Two -->
      <div class="hidden xmd:block">
        <div
          class="flex flex-row justify-start items-center space-x-6 pl-12 pt-4 2xl:space-x-8"
        >
          <nuxt-link
            v-for="(item, i) in navList"
            :key="i"
            :to="item.url"
            class="flex justify-center items-center text-lg lg:text-base font-bold text-primary-100 hover:text-secondary-100 border-b-2 border-transparent hover:border-secondary-100 custom-transition pb-1"
          >
            <span>{{ item.name }}</span>
            <span class="lg:hidden">({{ item.totalItem }})</span>
            <span
              v-if="item.tag"
              class="bg-secondary-a-100 text-white px-1 py-0.5 text-[.625rem] transform -translate-y-1 translate-x-1 rounded-lg h-4 flex justify-center items-center"
              >{{ item.tag }}</span
            >
          </nuxt-link>
        </div>
      </div>
    </div>

    <!-- Mobile side bar -->
    <div
      v-if="showMenu"
      class="fixed top-0 left-0 h-screen w-screen z-50 sm:pr-[60%] bg-gray-darkest bg-opacity-60"
    >
      <MobileSideMenu @close="toggleMenu" @showSearch="toggleSearchBox" />
    </div>

    <!-- search modal -->

    <div
      v-if="showSearchBox"
      class="fixed top-0 left-0 h-screen w-screen z-50 lg:pr-[60%] bg-gray-darkest bg-opacity-60"
    >
      <Search @close="toggleSearchBox" />
    </div>
  </header>
</template>

<script>
import MobileSideMenu from './MobileSideMenu.vue'
import Search from './Search.vue'

import CartModal from '@/components/header/CartModal.vue'
import ProfileModal from '@/components/header/ProfileModal.vue'
import Icons from '@/components/global/Icons.vue'

export default {
  components: {
    Icons,
    CartModal,
    ProfileModal,
    MobileSideMenu,
    Search,
  },
  data() {
    return {
      showMenu: false,
      showProfile: false,
      showCartModal: false,
      showSearchBox: false,
      showOthersAppList: false,
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
      topPanelMsg: '',
    }
  },
  methods: {
    toggleMenu() {
      this.showMenu = !this.showMenu
    },
    toggleProfile() {
      this.showProfile = !this.showProfile
    },
    toggleCartModal() {
      this.showCartModal = !this.showCartModal
    },
    toggleSearchBox() {
      this.showSearchBox = !this.showSearchBox
    },
    toggleOthersAppList() {
      this.showOthersAppList = !this.showOthersAppList
    },
    handleClickOutsideAppList() {
      this.showOthersAppList = false
    },
    handleClickOutsideProfile() {
      this.showProfile = false
    },
    handleClickOutsideCart() {
      this.showCartModal = false
    },
  },
}
</script>

<style scoped>
.header-icon-btn {
  @apply h-8 w-8 md:h-11 md:w-11 bg-none hover:bg-primary-5 rounded-full p-1 xl:flex justify-center items-center transition duration-300 ease-in-out;
}
</style>
