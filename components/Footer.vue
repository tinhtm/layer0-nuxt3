<template>
  <div id="footer">
    <footer class="bg-gray-lighter mt-5 py-10">
      <div class="px-5 mx-auto main:container xl:px-0">
        <div class="border-b border-t border-gray-light py-5">
          <button on:click="{toggleExpand}" class="flex items-center">
            <span class="py-2 tracking-wide mr-5">*Disclaimers</span>
            <SvgIcon
              :path="arrowChevronNext"
              :icon-class="`w-[20px] h-[20px] duration-700 cursor-pointer select-none ${
                !isExpand ? 'rotate-90' : 'rotate-[-90deg]'
              }`"
              fill="#2A363E"
            >
            </SvgIcon>
          </button>

          <div v-if="isExpand">
            <p class="mb-2">
              Disclaimer: The dietary and other substances, and/or materials,
              equipment or devices discussed on this site may not have undergone
              evaluation and/or testing by the United States Food and Drug
              Administration or like agency of any other country. Risks that
              might be determined by such testing are unknown.
              <nuxt-link
                class="font-bold text-gray-darkest hover:text-gray-darker hover:underline"
                to="/legal/earnings-disclaimer"
                >Click here</nuxt-link
              >
              to read the full disclaimer text.
            </p>
            <p>
              These statements have not been evaluated by the FDA. This product
              is not intended to diagnose, treat, cure or prevent any disease.
              Information on this site is provided for informational purposes
              only, it is not meant to substitute medical advice provided by
              your physician or any other medical professional. You should not
              use the information contained on this site for diagnosing or
              treating a health problem, disease, or prescribing any medication.
              Please read product label before use. Best results are only
              achieved when combined with diet and exercise program. Results not
              typical for any or all claims.
            </p>
          </div>
        </div>

        <!-- footer main content -->
        <div
          class="w-full py-8 xmd:py-10 divide-x-0 divide-gray-darkest xmd:flex xmd:items-center"
        >
          <nuxt-link to="/"
            ><img
              src="/images/logo.svg"
              alt="dr. berg logo"
              class="mr-2 h-[48px] xmd:mr-[56px] mb-5"
              height="48px"
              width="259.3"
          /></nuxt-link>

          <!-- social media icons -->
          <div class="flex items-center space-x-3 xxs:space-x-7">
            <a href="https://www.youtube.com/c/DrEricBergDC" target="_blank">
              <SvgIcon
                :path="iconYoutube"
                icon-class="w-[32px] h-[32px]"
                fill="#2A363E"
              />
            </a>
            <a href="https://www.facebook.com/drericberg" target="_blank">
              <SvgIcon
                :path="iconFacebook"
                icon-class="w-[32px] h-[32px]"
                fill="#2A363E"
              />
            </a>
            <a href="https://twitter.com/drericbergdc" target="_blank">
              <SvgIcon
                :path="iconTwitter"
                icon-class="w-[32px] h-[32px]"
                fill="#2A363E"
              />
            </a>
            <a href="https://www.pinterest.com/drericberg" target="_blank">
              <SvgIcon
                :path="iconPinterest"
                icon-class="w-[32px] h-[32px]"
                fill="#2A363E"
              />
            </a>
            <a href="https://www.instagram.com/drericberg" target="_blank">
              <SvgIcon
                :path="iconInstagram"
                icon-class="w-[32px] h-[32px]"
                transform="translate(-443px, -933px)"
                fill="#2A363E"
              />
            </a>
          </div>
        </div>

        <!-- navigation links -->
        <div class="grid grid-cols-1 xmd:grid-cols-4 mxl:w-8/12">
          <div v-for="(item, i) in links" :key="i" class="text-left mb-5">
            <p>
              <strong>{{ item.title }}</strong>
            </p>

            <div class="flex flex-col space-y-1 mt-4">
              <nuxt-link
                v-for="(child, z) in item.children"
                :key="z"
                :to="child.link"
                class="text-gray-darkest hover:text-gray-darker"
                >{{ child.text }}</nuxt-link
              >
            </div>
          </div>
        </div>

        <!-- copyright -->
        <div class="mt-[10px]">
          <p class="xmd:hidden">
            The Health & Wellness Center, Inc.<br /><strong>Address:</strong>
            4501 Ford Avenue, Alexandria, VA 22302.<br /><strong>Phone:</strong>
            703-354-7336
          </p>
          <p class="hidden xmd:block">
            The Health & Wellness Center, Inc. <strong>Address:</strong> 4501
            Ford Avenue, Alexandria, VA 22302.
            <strong>Phone:</strong> 703-354-7336
          </p>
          <p class="mt-2">
            © Copyright {{ new Date().getFullYear() }}. All rights reserved.
          </p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import SvgIcon from '@/components/global/SvgIcon.vue'
import {
  iconTwitter,
  iconFacebook,
  iconYoutube,
  iconPinterest,
  iconInstagram,
  arrowChevronNext,
} from '@/utils/icon.js'

export default {
  components: {
    SvgIcon,
  },

  data() {
    return {
      links: [
        {
          title: 'About',
          children: [
            {
              text: 'Dr. Berg',
              link: '/dr-eric-berg/bio',
            },
          ],
        },
        {
          title: 'Orders and shipping',
          children: [
            {
              text: 'My account',
              link: '/customer/account/login',
            },
            {
              text: 'Shipping methods',
              link: '/shipping-policy',
            },
            {
              text: 'Refunds',
              link: '/return-policy',
            },
          ],
        },
        {
          title: 'Support',
          children: [
            {
              text: 'Hours of operation',
              link: '#!',
            },
            {
              text: 'Contact us',
              link: '#!',
            },
            {
              text: 'Official resellers',
              link: 'pages/official-resellers-socialmedia.html#resellers',
            },
            {
              text: 'Official social media',
              link: '/pages/official-resellers-socialmedia.html#social',
            },
            {
              text: 'Wholesale application',
              link: '/pages/wholesale-application.html',
            },
          ],
        },
        {
          title: 'Legal',
          children: [
            {
              text: 'Terms and conditions',
              link: '/terms-and-conditions',
            },
            {
              text: 'Privacy policy',
              link: '/privacy-policy-cookie-restriction-mode',
            },
          ],
        },
      ],
      isExpand: false,
      iconTwitter,
      iconFacebook,
      iconYoutube,
      iconPinterest,
      iconInstagram,
      arrowChevronNext,
    }
  },

  methods: {
    toggleExpand() {
      this.isExpand = !this.isExpand
    },
  },
}
</script>

<style></style>
