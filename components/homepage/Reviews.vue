<template>
  <section class="pt-8 lg:pt-5 px-4 xl:px-0 pb-12">
    <h3 class="text-xl font-bold">On the Web</h3>
    <h4 class="text-2xl font-bold">4.89 Overall</h4>
    <p>Out of 21350 Reviews</p>

    <!-- slider -->
    <div class="mt-8">
      <Splide :options="options">
        <!-- googc3le -->
        <SplideSlide>
          <nuxt-link
            :to="items.google.url"
            class="flex justify-start items-center space-x-6 border px-7 py-6"
          >
            <img :src="items.google.image" alt="" />

            <div>
              <div class="flex justify-start items-center space-x-2">
                <span class="text-sm text-gray-dark inline-block mt-2"
                  >4.9</span
                >

                <div class="text-[#e2bf30] flex justify-start items-center">
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                </div>
              </div>

              <span
                class="text-sm font-bold underline underline-offset-1 hover:no-underline custom-transition"
                >View 4920 reviews</span
              >
            </div>
          </nuxt-link>
        </SplideSlide>

        <!-- trust spot -->
        <SplideSlide>
          <nuxt-link
            :to="items.trustspot.url"
            class="flex justify-start items-center space-x-6 border px-7 py-6"
          >
            <img :src="items.trustspot.image" alt="" />

            <div>
              <div class="flex justify-start items-center space-x-2">
                <span class="text-sm text-gray-dark inline-block mt-2"
                  >4.9</span
                >

                <div class="text-[#e2bf30] flex justify-start items-center">
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                  <img src="/images/homepage/community/icon_star.svg" alt="" />
                </div>
              </div>

              <span
                class="text-sm font-bold underline underline-offset-1 hover:no-underline custom-transition"
                >View 28750 reviews</span
              >
            </div>
          </nuxt-link>
        </SplideSlide>

        <!-- youtube -->
        <SplideSlide>
          <nuxt-link
            :to="items.youtube.url"
            class="flex justify-start items-center space-x-8 border px-7 py-6"
          >
            <div class="flex justify-start items-center space-x-4">
              <img :src="items.youtube.image" alt="" class="h-12" />

              <div>
                <span class="flex justify-start items-center space-x-1.5">
                  <span class="text-xs font-bold">{{
                    items.youtube.userName
                  }}</span>
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5"
                    viewBox="0 0 20 20"
                    fill="#0091A8"
                  >
                    <path
                      fill-rule="evenodd"
                      d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                      clip-rule="evenodd"
                    />
                  </svg>
                </span>

                <span class="text-[11px]">{{ items.youtube.publishDate }}</span>
              </div>
            </div>

            <span class="font-bold text-error-100">SUBSCRIBE 7.18 M</span>
          </nuxt-link>
        </SplideSlide>

        <!-- facebook -->
        <SplideSlide>
          <nuxt-link
            :to="items.facebook.url"
            class="flex justify-start items-center space-x-8 border px-7 py-6"
          >
            <div class="flex justify-start items-center space-x-4">
              <img :src="items.facebook.image" alt="" class="h-12" />

              <div>
                <span class="flex justify-start items-center space-x-1.5">
                  <span class="text-xs font-bold">{{
                    items.facebook.userName
                  }}</span>
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5"
                    viewBox="0 0 20 20"
                    fill="#D3D6D7"
                  >
                    <path
                      fill-rule="evenodd"
                      d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                      clip-rule="evenodd"
                    />
                  </svg>
                </span>

                <span class="text-[11px]">{{
                  items.facebook.publishDate
                }}</span>
              </div>
            </div>

            <div class="flex justify-start items-center space-x-4">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 448 512"
                height="40"
                width="40"
                fill="#395185"
              >
                <path
                  d="M400 32H48A48 48 0 0 0 0 80v352a48 48 0 0 0 48 48h137.25V327.69h-63V256h63v-54.64c0-62.15 37-96.48 93.67-96.48 27.14 0 55.52 4.84 55.52 4.84v61h-31.27c-30.81 0-40.42 19.12-40.42 38.73V256h68.78l-11 71.69h-57.78V480H400a48 48 0 0 0 48-48V80a48 48 0 0 0-48-48z"
                />
              </svg>
              <span class="text-[#395185]">Become a supporter</span>
            </div>
          </nuxt-link>
        </SplideSlide>
      </Splide>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      items: {
        google: {
          image: 'https://drberg-dam.imgix.net/others/google.jpg',
          rating: 0,
          url: 'https://www.google.com/maps/place/Dr.+Eric+Berg+DC/@16.8422557,159.9760726,3z/data=!3m1!4b1!4m7!3m6!1s0x89b7b31b4b25b92d:0xd751efa24a5143a1!8m2!3d45.5977671!4d-127.2696988!9m1!1b1',
        },
        trustspot: {
          image: 'https://drberg-dam.imgix.net/others/trustspot.png',
          rating: 0,
          url: 'https://trustspot.io/store/Dr-Berg-Nutritionals?product=1',
        },
        youtube: {
          image: 'https://drberg-dam.imgix.net/others/avatar.jpg',
          userName: 'DR. Eric Berg DC',
          publishDate: 'Published on Dec 15, 2016',
          url: 'https://www.youtube.com/user/drericberg123',
        },
        facebook: {
          image: 'https://drberg-dam.imgix.net/others/avatar2.jpg',
          userName: 'DR. Eric Berg',
          rating: 0,
          url: 'https://www.facebook.com/drericberg/',
        },
      },
      options: {
        arrows: false,
        pagination: false,
        gap: '1.5rem',
        autoWidth: true,
      },
    }
  },
}
</script>
