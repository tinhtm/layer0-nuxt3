<template>
  <svg
    aria-hidden="true"
    focusable="false"
    data-prefix="fab"
    data-icon="linkedin-in"
    class="{iconClass}"
    role="img"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 24 24"
    style="{iconStyle}"
  >
    <path :fill="fill" :d="path" :style="`transform: ${transform};`" />
  </svg>
</template>

<script>
export default {
  props: {
    fill: {
      type: String,
      default: '#013253',
    },
    iconClass: {
      type: String,
      default: '',
    },
    iconStyle: {
      type: String,
      default: '',
    },
    path: {
      type: String,
      default: '',
    },
    transform: {
      type: String,
      default: '',
    },
  },
}
</script>
