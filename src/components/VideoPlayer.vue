<script setup>
// import Aliplayer from 'aliyun-aliplayer'
// import 'aliyun-aliplayer/build/skins/default/aliplayer-min.css'
import Plyr from 'plyr';
import 'plyr/dist/plyr.css';
import { ref, defineProps, onMounted, onUnmounted } from 'vue';

const props = defineProps({
  src: String,
});
const player = ref();
const playerId = `video-player-${Math.random().toString(36).substr(2, 9)}`; // 生成唯一 ID

const createPlayer = (source, cover) => {
  player.value = new Plyr(`#${playerId}`, {
    controls: [
      'play-large',
      'play',
      'progress',
      'current-time',
      'mute',
      'volume',
      'captions',
      'fullscreen',
    ],
  });
  player.value.on('enterfullscreen', () => {
    console.log('enterfullscreen');
  });
  player.value.on('exitfullscreen', () => {
    console.log('exitfullscreen');
  });
};

onMounted(() => {
  createPlayer();
});
onUnmounted(() => {
  player.value.destroy();
});
</script>
<template>
  <video
    :src="src"
    :id="playerId"
    crossorigin
    playsinline
    data-plyr-config="{}"
  ></video>
</template>
