<template>
  <div class="p-4 md:rounded-sm md:mt-8 md:border rounded">
    <button
      class="font-bold flex justify-between items-center w-full"
      @click="expandTypes = !expandTypes"
    >
      <span>Product Type</span>
      <span
        class="transform custom-transition"
        :class="expandTypes ? 'rotate-0' : 'rotate-180'"
      >
        <Icons name="chevron" />
      </span>
    </button>

    <div v-if="expandTypes" class="space-y-6 mt-4">
      <div
        v-for="(item, i) in types"
        :key="i"
        class="relative flex justify-start items-center space-x-6 md:space-x-4 text-gray-darker md:-ml-4"
      >
        <input
          :id="`type-${i}`"
          type="checkbox"
          :name="`type-${i}`"
          :value="item.name"
          :group="selectedTypes"
          class="h-4 w-4 absolute top-.5 left-6 z-10 cursor-pointer opacity-0"
        />
        <span
          class="h-4 w-4 border border-gray-dark flex justify-center items-center rounded-sm text-white"
        >
          <Icons name="check-sign" class-list="h-3.5" />
        </span>
        <label
          :for="`type-${i}`"
          class="text-sm cursor-pointer whitespace-nowrap"
          >{{ item.name }} ({{ item.totalItem }})</label
        >
      </div>
    </div>
  </div>
</template>

<script>
import Icons from '@/components/global/Icons.vue'

export default {
  components: { Icons },

  data() {
    return {
      types: [],
      selectedTypes: [],
    }
  },

  methods: {
    handelChecked(e) {
      if (e.target.checked) {
        this.$emit('add-type', e.target.value)
      } else {
        this.$emit('remove-type', e.target.value)
      }

      console.log(this.selectedTypes)
    },
  },
}
</script>

<style scoped>
input[type='checkbox']:checked ~ span {
  @apply bg-[#0091a8];
}
</style>
