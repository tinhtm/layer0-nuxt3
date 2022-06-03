<template>
  <section class="pt-6">
    <h2 class="hidden xl:block">{{ data.name || '' }}</h2>

    <!-- review -->
    <div class="mt-6">
      <h5 class="hidden xl:block text-xs font-bold uppercase">
        Product Reviews
      </h5>

      <!-- stars and reviews -->
      <div
        class="mt-2 flex flex-col justify-center items-center xl:items-start"
      >
        <!-- stars -->
        <div class="text-[#e2bf30] flex justify-start items-center space-x-0.5">
          <Icons name="star" class-list="h-6 w-6" />
          <Icons name="star" class-list="h-6 w-6" />
          <Icons name="star" class-list="h-6 w-6" />
          <Icons name="star" class-list="h-6 w-6" />
          <Icons name="star" class-list="h-6 w-6" />
          <span class="text-primary-100 font-semibold pl-2">{{
            data.rating || 0
          }}</span>
        </div>

        <div class="text-secondary-100 text-sm whitespace-nowrap mt-2">
          <a
            href="#reviews"
            class="hover:underline custom-transition"
            on:click="{goToReviewSection}"
          >
            {{ data.reviews || 0 }} Reviews</a
          >

          <span> | </span>
          <a
            href="#reviews"
            class="hover:underline custom-transition"
            on:click="{goToWriteAReview}"
          >
            Write A Review
          </a>

          <span> | </span>
          <a
            href="#reviews"
            class="hover:underline custom-transition"
            on:click="{goToQuestionSection}"
          >
            Ask A Question</a
          >
        </div>
      </div>

      <!-- Benefits -->
      <div class="mt-8 hidden xl:block">
        <h4 class="text-xs font-bold uppercase">Benefits</h4>
        <p class="text-sm">{{ data.short_description }}</p>
      </div>
    </div>

    <h2 class="xl:hidden mt-4 text-xl">{{ data.name }}</h2>
  </section>
</template>

<script>
import Icons from '@/components/global/Icons.vue'

export default {
  components: { Icons },

  props: {
    data: {
      type: Object,
      required: true,
    },
  },

  methods: {
    goToQuestionSection() {
      this.$emit('go-to-question-section')
    },

    goToReviewSection() {
      this.$emit('go-to-review-section')
    },

    goToWriteAReview() {
      this.$emit('go-to-write-a-review')
    },
  },
}
</script>
