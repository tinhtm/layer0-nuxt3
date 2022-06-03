<template>
  <div class="flex justify-start items-start relative">
    <input
      :id="`item-${index}`"
      type="radio"
      :name="name"
      :group="selected"
      :value="item"
      class="h-6 w-6 z-[1] absolute top-0 left-0 opacity-0"
    />

    <span class="">
      <span
        class="h-2.5 w-2.5 inline-block ring-1 ring-offset-[3px] ring-secondary-100 rounded-full relative z-0 bg-white mr-4"
      />
    </span>

    <label :for="`item-${index}`" class="flex flex-col space-y-[6px] pb-1">
      <span class="font-bold">{{ item.title }}</span>
      <span class="text-sm text-gray-darker">{{ item.detail }}</span>
    </label>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
    item: {
      type: String,
      default: '',
    },
    reset: {
      type: Boolean,
      default: false,
    },
  },

  data() {
    return {
      selected: {},
    }
  },

  watch: {
    reset(reset) {
      if (!reset) {
        this.selected = {}
      }
    },
  },
}
</script>

<style scoped>
input[type='radio']:checked ~ span span {
  @apply bg-secondary-100;
}
</style>
