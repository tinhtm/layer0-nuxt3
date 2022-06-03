<template>
  <section id="faq" class="my-16">
    <h3 class="text-sm font-bold">FAQ</h3>

    <div class="border mt-1">
      <div v-for="(item, i) in faqs" :key="i" class="border-b px-4">
        <div class="py-3 text-sm">
          <div
            class="cursor-pointer flex justify-start items-center space-x-4 text-primary-100"
            @click="toggleShowAnswers(i)"
          >
            <span
              class="transform custom-transition"
              :class="showAnswers.includes(i) ? 'rotate-30' : '-rotate-90'"
            >
              <Icons name="chevron" />
            </span>
            <span>{{ item.question }}</span>
          </div>

          <p v-if="showAnswers.includes(i)" class="px-8 py-3">
            {{ item.answer }}
          </p>
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
      showAnswers: [],
      faqs: [
        {
          question: 'How should I use this product?',
          answer: 'Take 3 tablets three times per day, with or without meals.',
        },
        {
          question: 'What is the maximum daily dose?',
          answer:
            'Do not exceed the recommended dose. Do not take 3 tablets before bed.',
        },
        {
          question: 'Can I use this while doing Keto?',
          answer:
            'Yes! In fact, this supplement can help you to maximize your results on the keto diet. It can help you adapt faster to your new way of making fuel, it can help reduce the keto flu, and it can help prevent any other side effects of starting keto.',
        },
        {
          question: 'How big of a supply do I get with each order?',
          answer:
            'Each bottle contains 30 servings of Dr. Berg’s Nutritional Yeast. That is 270 tablets per bottle.',
        },
      ],
    }
  },

  methods: {
    toggleShowAnswers(index) {
      if (this.showAnswers.includes(index)) {
        this.showAnswers.splice(this.showAnswers.indexOf(index), 1)
        this.showAnswers = [...this.showAnswers]
        console.log(this.showAnswers)
      } else {
        this.showAnswers = [...this.showAnswers, index]
      }
    },
  },
}
</script>
