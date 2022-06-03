<template>
  <div
    class="rounded-xl border-2 border-gray-100 hover:border-[#58bccc4d]"
    :class="horizontalView && 'md:p-4'"
  >
    <div
      class="relative"
      :class="horizontalView && 'md:grid grid-cols-12 gap-x-2'"
    >
      <!-- Add to Wish List -->
      <button class="absolute top-4 left-4 group z-10">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6 hover:fill-gray-900"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M4.618 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
          />
        </svg>

        <span
          class="hidden px-2 py-2.2 bg-gray-900 text-white text-xs group-hover:block absolute top-6 left-6 whitespace-nowrap"
          >Add to Wish List</span
        >
      </button>

      <!-- Image -->
      <div class="mx-5 h-[19rem] {horizontalView && 'col-start-1 col-end-4'}">
        <nuxt-link :to="data.sku || '#!'">
          <img
            :src="data.thumbnail_image || ''"
            alt=""
            class="w-full h-full object-contain object-center"
          />
        </nuxt-link>
      </div>

      <div
        class="px-4 pb-6"
        :class="
          horizontalView &&
          'col-start-4 col-end-13 md:grid grid-cols-12 gap-x-2'
        "
      >
        <!-- review and description -->
        <div :class="horizontalView && 'col-start-1 col-end-10'">
          <!-- stars and reviews -->

          <div
            v-if="data.rating"
            :class="
              !horizontalView &&
              'flex flex-wrap justify-start items-center space-x-1 h-[2.5rem]'
            "
          >
            <!-- stars -->
            <div class="flex justify-start items-center space-x-0.5">
              <div
                class="text-[#e2bf30] flex justify-start items-center space-x-[1px]"
              >
                <Icons
                  v-show="0.5 <= data.rating && data.rating <= 5"
                  name="star"
                  class-list="h-4 w-4"
                />
                <Icons
                  v-show="data.rating < 0.5"
                  name="star-outline"
                  class-list="h-4 w-4"
                />

                <Icons
                  v-show="1.5 <= data.rating && data.rating <= 5"
                  name="star"
                  class-list="h-4 w-4"
                />
                <Icons
                  v-show="data.rating < 1.5"
                  name="star-outline"
                  class-list="h-4 w-4"
                />

                <Icons
                  v-show="2.5 <= data.rating && data.rating <= 5"
                  name="star"
                  class-list="h-4 w-4"
                />
                <Icons
                  v-show="data.rating < 2.5"
                  name="star-outline"
                  class-list="h-4 w-4"
                />

                <Icons
                  v-show="3.5 <= data.rating && data.rating <= 5"
                  name="star"
                  class-list="h-4 w-4"
                />
                <Icons
                  v-show="data.rating < 3.5"
                  name="star-outline"
                  class-list="h-4 w-4"
                />

                <Icons
                  v-show="4.5 <= data.rating && data.rating <= 5"
                  name="star"
                  class-list="h-4 w-4"
                />
                <Icons
                  v-show="data.rating < 4.5"
                  name="star-outline"
                  class-list="h-4 w-4"
                />
              </div>

              <span class="text-primary-100 text-xs font-semibold">{{
                data.rating
              }}</span>
            </div>

            <span v-if="horizontalView" class="text-secondary-100">|</span>

            <!-- review & questions -->
            <div>
              <nuxt-link
                :to="`${data.sku} + '#reviews'`"
                class="text-secondary-100 text-xs font-semibold whitespace-nowrap"
              >
                <span class="hover:underline">
                  {{ data.reviews || 0 }} Reviews</span
                ></nuxt-link
              >

              <nuxt-link
                v-if="horizontalView && data.questions"
                to="#!"
                class="text-secondary-100 text-xs font-semibold whitespace-nowrap"
                >| {{ data.questions }} Questions</nuxt-link
              >
            </div>
          </div>

          <div v-else class="h-[2.5rem]" />

          <!-- title & description -->
          <div class="min-h-[3rem] my-2.5">
            <nuxt-link
              :to="data.sku || ''"
              class="text-primary-100 font-semibold text-lg line-clamp-2 h-14 hover:underline"
              >{{ data.name }}</nuxt-link
            >

            <!-- stock indicator -->

            <div v-if="data.stockIndicator" class="pb-5 pt-5 space-y-2">
              <!-- Limited quantity -->

              <div
                v-if="data.limitedQty"
                class="flex justify-start items-center space-x-2"
              >
                <img src="/images/homepage/limitedQty.svg" alt="" />
                <span class="text-primary-cta-100 text-sm font-bold"
                  >Limited quantity</span
                >
              </div>

              <!-- stock alert -->

              <div
                v-if="data.stockAlert"
                class="flex justify-start items-center space-x-2"
              >
                <img src="/images/all-product/stock-1.svg" alt="" />
                <span class="text-error-100 text-sm font-bold"
                  >Stock alert! Last products</span
                >
              </div>

              <!-- very low qty -->

              <div
                v-if="data.lowQty"
                class="flex justify-start items-center space-x-2"
              >
                <img src="/images/all-product/stock-2.svg" alt="" />
                <span class="text-secondary-a-100 text-sm font-bold"
                  >Very low quantity!</span
                >
              </div>
            </div>

            <p
              v-if="horizontalView && data.description"
              class="text-xs text-secondary-100"
            >
              {{ data.description }}
            </p>
          </div>
        </div>

        <!-- price & view detials -->
        <div :class="horizontalView && 'col-start-10 col-end-13 text-right'">
          <!-- price -->
          <div>
            <div
              v-if="data.special_price"
              class="text-primary-100 text-xs mb-1"
            >
              <span class="line-through">${{ data.price }}</span>
              <span class="px-1 text-[0.7rem]">
                -{{ getDiscountPercent(data.price, data.special_price) }}%
              </span>
            </div>

            <span class="text-primary-100 font-bold"
              >${{ data.special_price ? data.special_price : data.price }}</span
            >
          </div>

          <!-- buttons -->
          <div class="mt-4">
            <button
              v-if="addToCartBtn"
              class="w-full py-3.5 border-2 border-secondary-a-100 rounded-sm text-secondary-a-100 font-bold hover:bg-secondary-a-100 hover:text-white transition-all duration-500 ease-in-out uppercase font-roboto"
            >
              Add to cart
            </button>

            <nuxt-link
              v-else
              :to="data.sku || '#!'"
              class="text-secondary-100 font-bold text-sm underline hover:no-underline"
              >View details »</nuxt-link
            >
          </div>
        </div>
      </div>
    </div>

    <!-- Bundle pack -->

    <div
      v-if="horizontalView && data.bundlePacks"
      class="hidden md:grid grid-cols-12 gap-x-2 bg-gray-lighter py-3 rounded"
    >
      <div
        class="col-start-4 col-end-13 px-4 flex justify-start items-center space-x-6"
      >
        <p class="text-xs font-semibold text-primary-100">
          Bundle pack available
        </p>
        <nuxt-link
          href="#!"
          class="text-secondary-100 text-xs underline hover:no-underline"
          >See details »</nuxt-link
        >
      </div>
    </div>
  </div>
</template>

<script>
import Icons from '@/components/global/Icons.vue'

export default {
  components: {
    Icons,
  },

  props: {
    data: {
      type: Object,
      default: null,
    },
    horizontalView: {
      type: Boolean,
      default: false,
    },
    addToCartBtn: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {}
  },

  methods: {
    getDiscountPercent(regularPrice, specialPrice) {
      return (((specialPrice - regularPrice) / regularPrice) * 100).toFixed(2)
    },
  },
}
</script>
