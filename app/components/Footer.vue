<script lang="ts" setup>
// @unocss-include

const socialMedia = [
  { platform: 'X', icon: 'i-nimiq:logos-twitter-mono', link: 'https://x.com/nimiq' },
  { platform: 'Discord', icon: 'i-nimiq:logos-discord-mono', link: 'https://discord.gg/cMHemg8' },
  { platform: 'Telegram', icon: 'i-nimiq:logos-telegram-mono', link: 'https://t.me/nimiq' },
  { platform: 'Reddit', icon: 'i-nimiq:logos-reddit-mono', link: 'https://www.reddit.com/r/Nimiq/' },
  { platform: 'GitHub', icon: 'i-nimiq:logos-github-mono', link: 'https://github.com/nimiq' },
  { platform: 'YouTube', icon: 'i-nimiq:logos-youtube-mono', link: 'https://www.youtube.com/c/Nimiq' },
  { platform: 'Nimiq Forum', icon: 'i-nimiq:logos-nimiq-forum-mono', link: 'https://forum.nimiq.community/' },
  { platform: 'Facebook', icon: 'i-nimiq:logos-facebook-mono', link: 'https://www.facebook.com/nimiq' },
  { platform: 'Instagram', icon: 'i-nimiq:logos-instagram-mono', link: 'https://www.instagram.com/wearenimiq/' },
]
</script>

<template>
  <footer class="dark !pt-0" data-section nq-no-px nq-no-max-width text-neutral-800>
    <!-- <div w-full children:max-w-690 border="y-1.5 white/10" p="x-32 y-40">
      <div mx-auto grid="~ cols-[auto_1px_auto_1fr] md:rows-2 gap-16 md:cols-[320px_1px_auto_auto] lg:cols-[1fr_auto_auto_auto_auto] items-center justify-center lg:rows-1">
        <span text="2xl white md:center" font-600 col-span="4" lg:hidden>Keep me updated</span>
        <span text="28 white" font-600 lh-none max-lg:hidden>Keep me updated</span>
        <NimiqNewsletterEmailInput col-span="4 md:1" relative max-h-33 max-w-7xl />
        <div hidden h-33 w-1 bg-neutral-500 md:block />
        <NuxtLink :to="socialMedia.at(0)!.link" size="36 lg:40" rounded-full transition-colors bg="white/8 hover:white/12" flex="~ items-center justify-center" title="X (Twitter)">
          <div :class="socialMedia.at(0)!.icon" text="14 white" />
        </NuxtLink>
        <NuxtLink :to="socialMedia.at(1)!.link" size="36 lg:40" rounded-full transition-colors bg="white/8 hover:white/12" flex="~ items-center justify-center" title="Discord">
          <div :class="socialMedia.at(1)!.icon" text="16 white" />
        </NuxtLink>
      </div>
    </div> -->

    <div class="disclaimer px-32 pt-80 md:text-center" border="t-1.5 white/10" md:w-full>
      <SectionLabel text="Legal Disclaimer" dark-mode class="mb-16 mt-48 text-left md:text-center" />
      <p text="22 white balance md:center" mx-auto class="max-w-[700px]">
        The content on this website must not be considered financial advice and does not constitute any offer or solicitation to offer or recommendation of any investment product.
      </p>
    </div>

    <div flex="~ col" text="sm neutral-700" px-32 nq-mt-96>
      <p text="md:center 2xl white">
        Follow us here
      </p>
      <ul role="list" flex="~ md:justify-center md:items-center gap-16 wrap" text="18 neutral-700" nq-mt-16>
        <li v-for="({ platform, icon, link }) in socialMedia" :key="platform || '123'" self-stretch justify-self-stretch aria-label="Links to some of our social media pages">
          <NuxtLink :title="platform" :to="link" focusable h-40 w-40 flex rounded-full p-10 bg="white/15 hocus:white/25" class="text-white" transition-colors :aria-label="`Visit Nimiq on ${platform}`">
            <div :class="icon" class="h-full w-full" />
          </NuxtLink>
        </li>
      </ul>

      <NuxtLink to="https://www.nimiq.com" group mt-72 w-max flex md:mx-auto>
        <div i-nimiq:logos-nimiq-horizontal-mono text="28 md:30 white/50 hover:white" transition-color />
      </NuxtLink>
      <p text="sm md:center left white/50" max-w-33ch md:mx-auto nq-mt-16>
        Nimiq is an Inuit word for an object or force that binds things together.
      </p>

      <div mt-16 flex="~ gap-16 wrap items-center" pb="32 md:64">
        <!-- <NuxtLink to="https://nimiq.com" font-semibold un-text="neutral-800 hocus:neutral-900" transition-colors>
          Imprint
        </NuxtLink>
        <div aria-hidden size-4 rounded-full bg-current op-40 /> -->
        <!-- <NuxtLink to="https://nimiq.com/cookie-policy" font-semibold un-text="neutral-800 hocus:neutral-900" transition-colors>
          Policy
        </NuxtLink>
        <div aria-hidden size-4 rounded-full bg-current op-40 /> -->
        <!-- <NuxtLink to="/#faq" font-semibold un-text="neutral-800 hocus:neutral-900" transition-colors>
          FAQ
        </NuxtLink> -->

        <p md:mx-auto>
          © Nimiq Foundation 2025
        </p>
      </div>
    </div>
  </footer>
</template>
