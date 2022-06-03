<template>
  <div class="pt-5 pb-4 px-5">
    <nuxt-link
      to="/"
      class="text-xs hover:underline underline-offset-1 custom-transition"
      >Home</nuxt-link
    >

    <template v-if="links.length">
      <span v-for="(item, i) in links" :key="i">
        <span> / </span>
        <nuxt-link :to="link.url" class="text-xs font-medium text-[#707070]">{{
          link.title
        }}</nuxt-link>
      </span>
    </template>
  </div>
</template>

<script>
export default {
  data() {
    return {
      links: [],
    }
  },
}
</script>
