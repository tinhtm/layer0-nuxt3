<template>
  <section id="reviews" class="pt-12 xl:px-4">
    <!-- heading -->
    <div
      class="bg-secondary-100 text-white flex flex-col justify-between p-4 xl:px-6"
    >
      <div class="flex justify-between items-center">
        <h4 class="flex justify-start items-center space-x-2">
          <span>Authentic Reviews By</span>
          <img src="/images/product/widget_logo.webp" alt="" />
        </h4>

        <button
          class="md:hidden"
          @click="showMobileButtons = !showMobileButtons"
        >
          <Icons name="menu" />
        </button>

        <div class="hidden md:flex justify-end items-center space-x-8">
          <button
            class="text-xs font-semibold px-4 py-1 uppercase"
            @click="showAskQuestion(true)"
          >
            Ask Question
          </button>
          <button
            class="text-xs font-semibold px-4 py-1 uppercase"
            @click="toggleWhiteAReview(true)"
          >
            Write a review
          </button>
        </div>
      </div>

      <div
        v-if="showMobileButtons"
        class="flex flex-col space-y-6 xl:space-x-6 pt-8 pb-4"
      >
        <button
          class="text-xs font-semibold px-4 py-1 uppercase"
          @click="showAskQuestion(true)"
        >
          Ask Question
        </button>
        <button
          class="text-xs font-semibold px-4 py-1 uppercase"
          @click="toggleWhiteAReview(true)"
        >
          Write a review
        </button>
      </div>
    </div>

    <div class="px-2 md:px-4">
      <!-- stars and reviews -->
      <StarsAndReviews />

      <AskQuestion
        v-if="showAskQuestionModal"
        @close="closeAskQuestionsModal"
      />

      <WriteAReview
        v-if="showWriteAReviewModal"
        @close="toggleWhiteAReview(false)"
      />

      <!-- Tabs -->
      <div class="mt-4 md:flex justify-between border-b pb-2">
        <div class="space-x-10">
          <button
            class="text-sm font-bold pb-1.5 border-b-[3px]"
            :class="
              currentTab === 'reviews'
                ? 'border-primary-100'
                : 'border-transparent'
            "
            @click="setCurrentTab('reviews')"
          >
            Product Reviews (738)
          </button>
          <button
            class="text-sm font-bold pb-1.5 border-b-[3px] {currentTab === 'questions' ? 'border-primary-100' : 'border-transparent'}"
            @click="setCurrentTab('questions')"
          >
            Questions (17)
          </button>
        </div>

        <!-- sort -->
        <div
          class="relative flex justify-end items-center space-x-3 mt-6 md:mt-0"
        >
          <span class="text-sm font-bold uppercase">Sort By:</span>

          <button
            class="flex justify-end items-center text-sm"
            @click="showSortList = !showSortList"
          >
            <span>Highest Rating</span>
            <Icons name="chevron" />
          </button>

          <!-- sort options -->
          <div
            v-if="showSortList"
            class="flex flex-col absolute top-5 right-0 bg-white rounded-xl py-2 overflow-hidden shadow-md"
          >
            <button
              v-for="(item, i) in sortOptions"
              :key="i"
              class="w-full text-left text-sm px-4 py-1 hover:bg-primary-60 hover:text-white"
              @click="setSort(item)"
            >
              {{ item }}
            </button>
          </div>
        </div>
      </div>

      <ProductReviews v-if="currentTab === 'reviews'" />

      <Questions v-if="currentTab === 'questions'" />
    </div>
  </section>
</template>

<script>
import AskQuestion from './AskQuestion.vue'
import ProductReviews from './ProductReviews.vue'
import Questions from './Questions.vue'
import StarsAndReviews from './StarsAndReviews.vue'
import WriteAReview from './WriteAReview.vue'
import Icons from '@/components/global/Icons.vue'

export default {
  components: {
    Icons,
    AskQuestion,
    ProductReviews,
    Questions,
    StarsAndReviews,
    WriteAReview,
  },

  props: {
    currentTab: {
      type: String,
      default: 'reviews',
    },
    showAskQuestionModal: {
      type: Boolean,
      default: false,
    },
    showWriteAReviewModal: {
      type: Boolean,
      default: false,
    },
  },

  data() {
    return {
      showMobileButtons: false,
      showSortList: false,
      selectedSort: 'Highest Rating',
      showWriteReviewBox: false,
      sortOptions: [
        'Most Recent',
        'Highest Rating',
        'Lowest Rating',
        'Most Votes',
        'Has Photo',
      ],
    }
  },

  methods: {
    setSort(item) {
      this.selectedSort = item.name
      this.showSortList = false
    },

    setCurrentTab(tab) {
      this.$emit('set-current-tab', tab)
    },

    showAskQuestion(val) {
      this.$emit('toggle-ask-question', val)
    },

    toggleWhiteAReview(val) {
      this.$emit('toggle-white-a-review', val)
    },

    closeAskQuestionsModal() {
      this.showAskQuestion(false)
    },
  },
}
</script>
