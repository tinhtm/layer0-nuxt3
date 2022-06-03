<template>
  <section class="pt-20 px-4 xl:px-0 md:grid grid-cols-2">
    <div class="aspect-w-1 aspect-h-1">
      <nuxt-link :to="data.url_path || '#!'">
        <img
          :src="data.thumbnail_image || ''"
          alt=""
          class="w-full object-contain object-center"
        />
      </nuxt-link>
    </div>

    <div class="flex flex-col justify-center">
      <h5 class="text-sm">INTRODUCING DR. BERG’S NEW FORMULA</h5>
      <h2 class="text-4xl mt-2">{{ data.name || '' }}</h2>
      <p class="text-sm mt-4" v-html="data.short_description || ''"></p>

      <nuxt-link
        :to="data.url_path || '#!'"
        class="text-lg text-secondary-100 font-medium mt-7 inline-block"
        >View details</nuxt-link
      >
    </div>
  </section>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      default: () => ({}),
    },
  },

  data() {
    return {}
  },
}
</script>
