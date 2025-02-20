<script lang="ts" setup>
import Identicons from '@nimiq/identicons/dist/identicons.bundle.min.js'

const props = defineProps({
  cardType: String,
  address: String,
  identiconSvg: String,
  reducedMovement: {
    type: Boolean,
    required: false,
    default: false,
  },
})

if (!props.address && !props.identiconSvg) {
  throw new Error('TiltCard requires either :address or :identiconSvg')
}

const identiconColor = ref<string>()
const $identicon = ref<HTMLDivElement>()

onMounted(() => {
  // Render card with Identicon
  nextTick(async () => {
    const svg: string = props.identiconSvg || await Identicons.svg(props.address)
    $identicon.value!.innerHTML = svg
    nextTick(() => {
      // Extract color of background <rect> element and apply to 'identiconColor' ref for use by card svg elements
      const backgroundColor = $identicon.value!.querySelector('svg rect[fill]')!.getAttribute('fill')!
      identiconColor.value = backgroundColor
      // remove <rect> element for plain identicon
      $identicon.value!.querySelector('svg rect')!.remove()
    })
  })
})
</script>

<template>
  <div class="relative overflow-hidden rounded-12">
    <template v-if="cardType === 'platinum'">
      <NuxtImg src="/img/cards/platinum-card-backdrop.png" class="absolute left-0 top-0 z-0 h-full w-full" alt="" />
    </template>
    <template v-else>
      <NuxtImg src="/img/cards/card-backdrop-rays.png" class="absolute left-0 top-0 z-0 h-full w-full" alt="" />
      <div class="absolute left-0 top-0 z-0 h-full w-full mix-blend-color" :style="`background-color: ${identiconColor};`" />
    </template>
    <NuxtImg :src="`/img/cards/${cardType}-card-frame.png`" class="relative z-1 h-full w-full" alt="" srcset="" />
    <IdenticonCardHex class="left-1/2 top-[19%] z-4 h-fit w-1/2 !absolute -translate-x-1/2" :type="cardType" :color="identiconColor" />
    <div ref="$identicon" class="identicon-box absolute left-1/2 top-[17%] z-5 w-1/2 scale-75 -translate-x-1/2" />
    <NuxtImg
      class="metal-grain absolute left-0 top-0 z-6 h-full w-full" src="/img/metal-grain.png" alt="" srcset=""
    />
  </div>
</template>

<style scoped>
.identicon-box :deep(svg) {
  width: 100%;
  height: 100%;
}

.metal-grain {
  mix-blend-mode: difference;
  filter: invert(1) brightness(1.1);
}
</style>
