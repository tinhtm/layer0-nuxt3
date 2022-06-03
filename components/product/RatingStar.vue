<template>
  <div class="flex justify-start items-center text-primary-100">
    <Icons name="star" class-list="h-6 w-6 fill-currentColor" />

    <Icons
      v-if="noOfStar > 1"
      name="star"
      class-list="h-6 w-6 fill-currentColor"
    />
    <Icons
      v-if="noOfStar > 2"
      name="star"
      class-list="h-6 w-6 fill-currentColor"
    />
    <Icons
      v-if="noOfStar > 3"
      name="star"
      class-list="h-6 w-6 fill-currentColor"
    />
    <Icons
      v-if="noOfStar > 4"
      name="star"
      class-list="h-6 w-6 fill-currentColor"
    />
  </div>
</template>

<script>
import Icons from '@/components/global/Icons.vue'

export default {
  components: { Icons },

  data() {
    return {
      noOfStar: 1,
    }
  },
}
</script>
