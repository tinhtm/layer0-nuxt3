<template>
  <div class="pt-6">
    <p class="text-xs uppercase font-bold">Product Options</p>

    <div v-for="(item, i) in data.tier_prices" :key="i" class="mt-4 flex justify-start items-start relative">
      <input
        :id="'product-option-' + (i + 1)"
        type="radio"
        name="product-options"
        :checked="selectedOption === item"
        :value="selectedOption"
        class="h-6 w-6 z-[1] absolute top-0 left-0 opacity-0"
        @change="onSelectItem(item)"
      />

      <span>
        <span
          class="ml-2 h-3 w-3 inline-block ring-1 ring-offset-[4px] ring-primary-100 rounded-full relative z-0 bg-white mr-4"
        />
      </span>

      <label :for="'product-option-' + (i + 1)">
        <span class="text-sm">{{ item.qty }} </span>

        <span class="text-sm text-secondary-100">(${{ item.value }}/unit)</span>
        <span class="bg-primary-40 text-white text-xs font-medium rounded px-2 py-1"
          >-{{ getDiscountPerc(item.value) }}%</span
        >
      </label>
    </div>
  </div>
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
    return {
      productOptions: [
        {
          unit: 1,
          unitType: 'bottle',
          price: 26.99,
          discount: 18.97,
        },
        {
          unit: 3,
          unitType: 'bottles',
          price: 25.99,
          discount: 21.98,
        },
      ],
    }
  },

  computed: {
    selectedOption() {
      return this.productOptions[0]
    },

    getDiscountPerc() {
      return (price) => {
        if (price) {
          return Math.round((1 - price / this.data.price) * 100)
        } else {
          return 0
        }
      }
    },
  },

  mounted() {
    console.log(this.data)
  },

  methods: {
    onSelectItem(item) {
      this.$emit('on-select-activity-level', item)
    },
  },
}
</script>

<style scoped>
input[type='radio']:checked ~ span span {
  @apply bg-primary-100;
}
</style>
