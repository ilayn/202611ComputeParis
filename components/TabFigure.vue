<!-- An image with its label on a small tab sticking out of the top-left edge, like a folder tab.
     Usage: <TabFigure src="/figures/x.png" label="Before" class="w-80" />
     A width class goes on the whole figure; the image fills it. -->
<script setup lang="ts">
defineProps<{
  src: string
  label: string
}>()
</script>

<template>
  <figure class="m-0 flex flex-col items-start">
    <figcaption class="px-3 py-0.5 text-sm font-600 rounded-t-md bg-[var(--frost2)] text-[var(--dark0)]">
      {{ label }}
    </figcaption>
    <img :src="src" :alt="label" class="w-full border-3 border-[var(--frost2)] rounded-b-md rounded-tr-md">
  </figure>
</template>
