<template>
  <section class="pt-8 lg:pt-5 px-4 xl:px-0 pb-12">
    <div class="bg-gray-lighter p-5 rounded-sm">
      <div>
        <h3 class="text-xl font-bold text-center text-primary-100">
          5 million + Keto community
        </h3>
        <p class="text-xs text-gray-dark text-center mt-4">
          Join our 5+ Million members. You will receive our latest news.
        </p>
      </div>

      <div class="mt-6 md:flex justify-between items-stretch max-w-2xl mx-auto">
        <input
          type="email"
          placeholder="ENTER YOUR EMAIL"
          :value="email"
          class="px-6 py-3 border w-full bg-white"
        />
        <button
          class="bg-primary-100 text-white flex justify-center items-center space-x-4 w-full px-6 py-3 uppercase md:w-auto md:py-4"
          @click="onSubscribtion"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
            />
          </svg>
          <span> Subscribe </span>
        </button>
      </div>

      <p v-if="error" class="max-w-2xl mx-auto text-sm text-error-100">
        {{ error }}
      </p>
    </div>

    <!-- toast message -->
    <div
      v-if="success"
      class="fixed top-20 lg:top-32 left-0 right-0 width-1260 border text-[#006400] bg-success-10 px-6 py-3 rounded border-none fill-current flex justify-center items-center space-x-2"
    >
      <Icons name="check" class-list="fill-current" />
      <span>Thank you for your subscription.</span>
    </div>
  </section>
</template>

<script>
import Icons from '@/components/global/Icons.vue'

export default {
  components: { Icons },

  data() {
    return {
      email: '',
      error: '',
      success: false,
    }
  },

  methods: {
    onSubscribtion() {
      this.error = ''
      if (this.email) {
        if (this.validateEmail(this.email)) {
          this.success = true

          setTimeout(() => {
            this.success = false
          }, 3000)
        } else {
          this.error =
            'Please enter a valid email address (Ex: johndoe@domain.com).'
        }
      } else {
        this.error = 'This is a required field.'
      }
    },

    validateEmail(email) {
      return String(email)
        .toLowerCase()
        .match(
          /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
        )
    },

    clearToast() {
      this.success = false
    },
  },
}
</script>
