<template>
  <div class="relative">
    <div class="width-1260 px-4">
      <Breadcrumb :links="breadcrumb" />

      <div class="xl:grid grid-cols-12 gap-x-6">
        <div class="col-start-1 col-end-5">
          <Slider :data="product.media_gallery_entries || []" />
        </div>

        <div class="col-start-5 col-end-10">
          <ProductSummary :data="product" />
        </div>

        <div class="col-start-10 col-end-13">
          <Pricing :data="product" />
        </div>
      </div>
    </div>

    <!-- sticky nav -->
    <div class="bg-primary-100 pt-3 text-gray-light sticky top-16 w-full xl:top-28 z-50">
      <div class="width-1260 px-4 text-sm font-bold flex justify-start items-center space-x-8 overflow-x-auto">
        <nuxt-link
          v-for="(item, i) in navItems"
          :key="i"
          :to="`#${item.id}`"
          class="pb-2 border-b-[4px] inline-block whitespace-nowrap custom-transition"
          :class="currentNavItem === item.id ? 'border-white text-white' : 'border-transparent'"
          @click="currentNavItem = item.id"
          >{{ item.name }}</nuxt-link
        >
      </div>
    </div>

    <div class="width-1260 px-4 py-4">
      <BundlePacks />
      <Videos />
      <AuthenticReviews />

      <Faq />
      <Subscribe />
    </div>
  </div>
</template>

<script>
import Breadcrumb from '@/components/global/Breadcrumb.vue'
import AuthenticReviews from '@/components/product/AuthenticReviews.vue'
import BundlePacks from '@/components/product/BundlePacks.vue'
import Pricing from '@/components/product/Pricing.vue'
import ProductSummary from '@/components/product/ProductSummary.vue'
import Slider from '@/components/product/Slider.vue'
import Videos from '@/components/product/Videos.vue'
import Faq from '@/components/product/Faq.vue'
import Subscribe from '@/components/homepage/Subscribe.vue'

export default {
  components: {
    Breadcrumb,
    AuthenticReviews,
    BundlePacks,
    Pricing,
    ProductSummary,
    Slider,
    Videos,
    Faq,
    Subscribe,
  },

  async setup() {
    const { data } = await useAsyncData('product', async () => {
      const route = useRoute()

      const sku = route.params.sku || ''

      const res = await fetch('https://edm-drberg.azurewebsites.net/api/products/detailProducts/' + sku)

      const data = await res.json()

      return {
        product: data.data || {},
      }
    })

    console.log(data._value)

    return {
      product: data._value.product,
    }
  },

  data() {
    return {
      currentNavItem: 'bundlePacks',
      navItems: [
        { name: 'BUNDLE PACKS', id: 'bundlePacks' },
        { name: 'DETAILS', id: 'details' },
        { name: 'VIDEOS', id: 'videos' },
        { name: 'REVIEWS', id: 'reviews' },
        { name: 'FAQ', id: 'faq' },
      ],
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
