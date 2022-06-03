<template>
  <section class="pt-5 px-4 xl:px-0">
    <h3 class="text-xl font-bold text-primary-100 uppercase">Explore drberg</h3>

    <div class="overflow-x-scroll hide-scrollbar">
      <div
        class="mt-4 flex justify-start space-x-4 md:space-x-0 md:grid grid-cols-2 md:gap-4 lg:grid-cols-4"
      >
        <div
          v-for="(item, i) in items"
          :key="i"
          class="shadow-md my-1 rounded md:grid grid-cols-6 gap-2 xl:shadow-none hover:shadow-md custom-transition"
        >
          <div
            class="h-20 w-28 overflow-hidden md:h-full md:col-start-1 col-end-3 md:w-full"
          >
            <img
              :src="item.image || ''"
              alt=""
              class="object-cover w-full h-full object-left"
            />
          </div>

          <div
            class="px-2 py-2 md:col-start-3 md:col-end-7 md:flex flex-col justify-center md:space-y-2"
          >
            <h4
              class="text-xs text-primary-100 md:text-black font-bold uppercase"
            >
              {{ item.name || '' }}
            </h4>
            <p class="text-xs text-gray-500 hidden md:block">
              {{ item.description || '' }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          name: 'SUPPLEMENTS',
          description:
            'Nutrient-dense and mineral rich. High quality source ingredients.',
          url: '/supplements',
          image: 'https://drberg-dam.imgix.net/product-images/supplements.jpg',
        },
        {
          name: 'PACKAGES & KITS',
          description:
            'Body Type Packages and Kits, Uniquely formulated by Dr Berg',
          url: '/bundles',
          image:
            'https://drberg-dam.imgix.net/product-images/packages-and-kits.jpg',
        },
        {
          name: 'BOOKS',
          description:
            'Author of the best selling The 7 Principles of Fat Burning',
          url: '/books',
          image: 'https://drberg-dam.imgix.net/product-images/books.jpg',
        },
        {
          name: 'DIGITAL PROGRAMS',
          description: 'Exclusive Membership, Coaching, Meal Maker and Keto',
          url: '/digital-programs',
          image:
            'https://drberg-dam.imgix.net/product-images/digital-programs.jpg',
        },
      ],
    }
  },
}
</script>
