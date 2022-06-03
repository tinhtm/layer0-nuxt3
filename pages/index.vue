<template>
  <div class="width-1260">
    <ExploreDrBerg />
    <FeaturedProduct :data="featuredProducts" />
    <NewestProducts :data="newestProducts" />
    <DontBeAStranger />
    <RecommendedProducts :data="recommendedProducts" />
    <SuccessStories />
    <InTheSpotlight :data="spotlightProducts" />
    <BeAPartOfOurCommunity />
    <Reviews />
    <Subscribe />
  </div>
</template>

<script>
import BeAPartOfOurCommunity from '@/components/homepage/BeAPartOfOurCommunity.vue'
import DontBeAStranger from '@/components/homepage/DontBeAStranger.vue'
import ExploreDrBerg from '@/components/homepage/ExploreDrBerg.vue'
import InTheSpotlight from '@/components/homepage/InTheSpotlight.vue'
import NewestProducts from '@/components/homepage/NewestProducts.vue'
import RecommendedProducts from '@/components/homepage/RecommendedProducts.vue'
import Reviews from '@/components/homepage/Reviews.vue'
import Subscribe from '@/components/homepage/Subscribe.vue'
import SuccessStories from '@/components/homepage/SuccessStories.vue'
import FeaturedProduct from '@/components/homepage/FeaturedProduct.vue'

export default {
  components: {
    BeAPartOfOurCommunity,
    DontBeAStranger,
    ExploreDrBerg,
    InTheSpotlight,
    NewestProducts,
    RecommendedProducts,
    Reviews,
    Subscribe,
    SuccessStories,
    FeaturedProduct,
  },

  async setup() {
    const { data } = await useAsyncData('homepage', async () => {
      const featuredProd = await fetch(
        'https://edm-drberg.azurewebsites.net/api/products/featuredProducts/s-gs-rl-p-56s'
      )

      const newProd = await fetch(
        'https://edm-drberg.azurewebsites.net/api/products/viewTypeProducts?viewType=Newest&pageSize=4'
      )

      const recommendedProd = await fetch(
        'https://edm-drberg.azurewebsites.net/api/products/viewTypeProducts?viewType=Recommended&pageSize=5'
      )

      const spotlightProd = await fetch(
        'https://edm-drberg.azurewebsites.net/api/products/viewTypeProducts?viewType=Spotlight&pageSize=5'
      )

      const newestProducts = await newProd.json()
      const featuredProducts = await featuredProd.json()
      const recommendedProducts = await recommendedProd.json()
      const spotlightProducts = await spotlightProd.json()

      return {
        newestProducts: newestProducts.data || [],
        featuredProducts: featuredProducts.data || [],
        recommendedProducts: recommendedProducts.data || [],
        spotlightProducts: spotlightProducts.data || [],
      }
    })

    return {
      newestProducts: data._value.newestProducts,
      featuredProducts: data._value.featuredProducts,
      recommendedProducts: data._value.recommendedProducts,
      spotlightProducts: data._value.spotlightProducts,
    }
  },
}
</script>
