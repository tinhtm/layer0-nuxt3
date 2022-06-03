<template>
  <div class="flex">
    <div class="relative flex justify-center items-center">
      <input
        id="one-time-purchase"
        type="radio"
        name="one-time-purchase"
        class="h-6 w-6 z-[1] absolute top-1/2 left-0 opacity-0 transform -translate-y-1/2"
      />

      <span class="">
        <span
          class="ml-2 h-3 w-3 inline-block ring-1 ring-offset-[4px] ring-primary-100 rounded-full relative z-0 bg-white mr-4"
        />
      </span>
    </div>

    <label for="one-time-purchase" class="flex flex-col pb-1">
      <p class="font-bold">One-time purchase</p>
      <span class="text-sm text-gray-darker line-through"
        >${{ data.price }}</span
      >

      <span>
        <span class="text-sm text-secondary-100"
          >${{ data.special_price }}</span
        >
        <span
          class="bg-primary-40 text-white text-xs font-medium rounded-xl px-2 py-1"
          >Saving {{ getPerc }}%</span
        >
      </span>
    </label>
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
    return {}
  },

  computed: {
    getPerc() {
      if (this.data) {
        return Math.round((1 - this.data.special_price / this.data.price) * 100)
      } else {
        return 0
      }
    },
  },

  methods: {
    onSelectActivityLevel(selected) {
      this.$emit('on-select-activity-level', selected)
    },
  },
}
</script>

<style scoped>
input[type='radio']:checked ~ span span {
  @apply bg-primary-100;
}
</style>
