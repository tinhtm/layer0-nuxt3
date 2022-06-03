<template>
  <section>
    <section class="pt-8 lg:pt-5 px-4 xl:px-0 pb-12">
      <h2 class="text-xl font-bold uppercase text-[#333]">Success Stories</h2>
      <h3 class="text-[28px] text-secondary-100 leading-[30px] font-bold">
        Dr. Berg is one of the most trusted sources of health information on the
        internet.
      </h3>

      <div class="mt-10 md:grid grid-cols-2 gap-12 space-y-6 md:space-y-0">
        <div id="story-slider" class="md:pt-8 xl:pt-0">
          <!-- test -->
          <Splide :options="options" @splide:active="setCurrentSilde">
            <SplideSlide v-for="(story, i) in successStories" :key="i">
              <!-- <div> -->
              <img
                :src="story.image"
                alt=""
                class="transform translate-y-1/2 rounded custom-transition"
              />
              <!-- </div> -->
            </SplideSlide>
          </Splide>
        </div>

        <!-- details -->
        <div class="flex flex-col justify-center">
          <p class="text-gray-darker font-bold">{{ currentSlider.name }}</p>
          <p class="text-gray-dark text-sm">{{ currentSlider.storySource }}</p>
          <p class="text-primary-100 font-semibold mt-4 text-justify">
            {{ currentSlider.description }}
          </p>

          <p>{{ currentSliderIndex + 1 }}/{{ successStories.length }}</p>
        </div>
      </div>
    </section>
  </section>
</template>

<script>
export default {
  data() {
    return {
      successStories: [
        {
          image:
            'https://drberg-dam.imgix.net/customer-images/Krista_Simpkins_copy_1.jpg',
          name: 'KRISTA SIMPKINS.',
          storySource: 'on: drberg.com',
          description:
            'I’ve spent most of my adult being overweight in some capacity, and probably just like you, I tried all the diets.  I’ve counted calories.  I’ve joined Weight Watchers multiple times.  Yes, I’d lose some weight initially, but it would always come back and I’d end up heavier than I was when I started.',
        },
        {
          image: 'https://drberg-dam.imgix.net/customer-images/JohnT.jpg',
          name: 'JOHN T.',
          storySource: 'on: Youtube',
          description:
            'My turn ... I hit my ""scale weight goal"" went from 210 to 159 and been on maintenance for a while. I was happy at 165 and under but last 2-3 weeks just tightened it up a bit and got below the 160 mark! Just for reference I\'m 5\'7 just under the 40 year mark and when we did the measurements for body fat started at about 26-28%, size 36-38 waist. I\'m now closer to the 40 year mark',
        },
        {
          image:
            'https://drberg-dam.imgix.net/customer-images/ChristopherG_2.jpg',
          name: 'CHRISTOPHER G.',
          storySource: 'on: Trustpost',
          description:
            "I owe all this to following a whole foods based, ketogenic (at times just low carb) diet, intermittent and longer term fasting as well as HIIT/weight training... I'm down 135lb on the scale, lost more body fat, gained muscle and feel like I've even aged backwards a little, lol. My main point is that stalls will happen. You might stumble here and there, but if you want it badly enough and keep at it, it is absolutely possible to start living a life you once thought was impossible. Be consistent, stay patient and trust the process.",
        },
        {
          image: 'https://drberg-dam.imgix.net/customer-images/jasonh.jpg',
          name: 'JASON H.',
          storySource: 'on: drberg.com',
          description:
            'I started Keto at the end of January 2019. I weighed 305 lbs. it is now November 5, 2019 and I weigh 214 lbs. so, 91 lbs in 9 months. I have followed Dr. Bergs suggestions/plan since day 1. I never cheated once. My wife introduced me to Keto and Dr. Berg and I’m so glad she did. Keto has absolutely changed my life.I Have Never Felt So Good In My Life. I Plan On Staying In Ketosis The Rest Of My Life!',
        },
        {
          image: 'https://drberg-dam.imgix.net/customer-images/EdelH.jpg',
          name: 'EDEL T.',
          storySource: 'on: Facebook',
          description:
            'I started my keto journey for better health. My main goal was not weightloss. That was a happy side effect I was sick and tired of feeling sick and tired so something had to change. Today I choose better. I choose not to eat the junk food I choose not to drink the soda I choose to eat good wholesome good I choose to eat the fat! I choose a better me!',
        },
      ],
      options: {
        type: 'loop',
        arrows: true,
        pagination: false,
        gap: '.5rem',
        padding: {
          left: '70%',
        },
      },
      currentSliderIndex: 0,
    }
  },

  computed: {
    currentSlider() {
      return this.successStories[this.currentSliderIndex]
    },
  },

  methods: {
    setCurrentSilde(val) {
      this.currentSliderIndex = val.index || 0
    },
  },
}
</script>

<style scoped>
#story-slider >>> .splide__slide.is-active img {
  transform: translateY(0) !important;
}
</style>
