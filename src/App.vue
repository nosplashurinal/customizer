<template>
  <div id="app">
    <Canvas :width="width" :height="height" :images="images" />
    <Controller />
  </div>
</template>

<script>
import loadImage from 'image-promise';
import Canvas from './components/Canvas';
import Controller from './components/Controller';

const images = [
  './static/body/body_1_1.png',
  './static/body/body_1_2.png',
  './static/body/body_1_3.png',
  './static/body/body_1_4.png',
  './static/top/top_1_1.png',
  './static/top/top_1_2.png',
  './static/top/top_1_3.png',
  './static/top/top_1_4.png',
  './static/number/NUM_1_1.png',
  './static/number/NUM_1_2.png',
  './static/number/NUM_1_3.png',
  './static/number/NUM_1_4.png',
];

export default {
  name: 'App',
  components: {
    Canvas,
    Controller
  },
  data() {
    return {
      isLoadedImages: !1,
      width: window.innerWidth,
      height: window.innerHeight,
      images: null,
    };
  },
  beforeCreate() {
    loadImage(images)
      .then((allImgs) => {
        /* eslint-disable-next-line */
        this.images = allImgs;
        this.isLoadedImages = !0;
      })
      .catch((err) => {
        /* eslint-disable-next-line */
        console.error('One or more images have failed to load :(');
        /* eslint-disable-next-line */
        console.error(err.errored);
        /* eslint-disable-next-line */
        console.info('But these loaded fine:');
        /* eslint-disable-next-line */
        console.info(err.loaded);
      });
  },
};
</script>

<style lang="scss">
@import './styles/reset.css';

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
