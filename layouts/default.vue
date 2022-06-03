<template>
  <div>
    <div class="fixed top-0 left-0 right-0 z-50 shadow-md transform">
      <Header />
    </div>

    <main class="pt-20 lg:pt-32">
      <slot></slot>
    </main>

    <Footer />
  </div>
</template>

<script>
import Footer from '@/components/Footer.vue'
import Header from '@/components/Header.vue'

export default {
  components: {
    Footer,
    Header,
  },
}
</script>

<style></style>
