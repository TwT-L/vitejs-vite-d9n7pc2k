<script setup>
import VideoPlayer from './components/VideoPlayer.vue';
const list = [
  {
    position: 'left',
    src: 'https://stream7.iqilu.com/10339/upload_transcode/202002/18/20200218093206z8V1JuPlpe.mp4',
  },
  {
    position: 'right',
    src: 'https://stream7.iqilu.com/10339/upload_transcode/202002/18/20200218093206z8V1JuPlpe.mp4',
  },
];
</script>

<template>
  <div class="mx-auto w-[400px] bg-gray-100 overflow-hidden px-4">
    <div
      v-for="(item, index) in list"
      :key="index"
      class="flex my-10 px-12 relative"
    >
      <div class="absolute top-0 left-0 overflow-auto inline-block">
        <div
          class="rounded-full w-10 h-10 bg-gray-400"
          v-if="item.position === 'left'"
        ></div>
      </div>
      <div class="grow">
        <div
          class="flex items-end"
          :class="{ 'flex-row-reverse': item.position === 'right' }"
        >
          <VideoPlayer :src="item.src"></VideoPlayer>
        </div>
      </div>
      <div class="absolute top-0 right-0 overflow-auto inline-block">
        <div
          class="rounded-full w-10 h-10 bg-gray-400"
          v-if="item.position === 'right'"
        ></div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
