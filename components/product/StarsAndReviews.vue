<template>
  <section>
    <div
      class="w-10/12 md:w-full xl:w-1/2 md:grid grid-cols-3 xl:grid-cols-2 md:py-4"
    >
      <div class="mt-2 flex flex-col justify-center items-start md:border-r">
        <!-- stars -->
        <div class="text-[#e2bf30] flex justify-start items-center space-x-0.5">
          <Icons name="star" class-list="h-10 w-10" />
          <Icons name="star" class-list="h-10 w-10" />
          <Icons name="star" class-list="h-10 w-10" />
          <Icons name="star" class-list="h-10 w-10" />
          <Icons name="star" class-list="h-10 w-10" />
        </div>

        <div class="text-sm whitespace-nowrap mt-2">
          <p class="hover:underline custom-transition text-lg font-bold">
            738 Reviews
          </p>
          <p class="hover:underline custom-transition mt-1 font-semibold">
            17 Questions, 17 Answers
          </p>
        </div>
      </div>

      <!-- star -->
      <div class="flex flex-col-reverse mt-4 md:px-3 lg:pl-10 xl:pl-3">
        <div
          v-for="(item, i) in starCount"
          :key="i"
          class="flex justify-between items-center py-1"
        >
          <span class="whitespace-nowrap w-11 text-xs uppercase"
            >{{ i + 1 }} star</span
          >

          <div
            class="relative pt-2 bg-gray-light rounded-md w-40 md:w-[6.5rem] lg:w-40"
          >
            <span
              class="absolute top-0 left-0 h-full rounded-md bg-secondary-100 {`w-[${getWidth( item )}%]`}"
              :style="`width: ${getWidth(item)}%`"
            />
          </div>

          <span class="w-14 text-xs text-gray-base">{{ item }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Icons from '@/components/global/Icons.vue'

export default {
  components: {
    Icons,
  },

  data() {
    return {
      starCount: [0, 0, 40, 101, 597],
    }
  },

  computed: {
    getWidth() {
      return (item) => {
        let total = 0

        this.starCount.forEach((item) => {
          total = total + item
        })

        return (item * 100) / total
      }
    },
  },
}
</script>
