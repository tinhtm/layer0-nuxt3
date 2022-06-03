<template>
  <section class="p-6">
    <p class="text-gray-darkest font-bold text-lg">Your Profile</p>
    <p class="mt-1">Welcome {{ userName }}</p>

    <div class="mt-6 space-y-4 flex flex-col">
      <nuxt-link
        to="/customer/account"
        class="hover:text-secondary-100 custom-transition"
        >Profile details</nuxt-link
      >
      <nuxt-link
        to="/sales/order/history"
        class="hover:text-secondary-100 custom-transition"
        >Orders</nuxt-link
      >
      <nuxt-link
        to="/wishlist"
        class="hover:text-secondary-100 custom-transition"
        >Orders</nuxt-link
      >
      <nuxt-link
        to="/customer/account/logout-success"
        class="hover:text-secondary-100 custom-transition"
        >Sign out</nuxt-link
      >
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      userName: 'John',
    }
  },
}
</script>
