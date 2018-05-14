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
  './static/pant_low/1.png',
  './static/pant_low/2.png',
  './static/pant_low/3.png',
  './static/pant_low/4.png',
  './static/pant_main/1.png',
  './static/pant_main/2.png',
  './static/pant_main/3.png',
  './static/pant_main/4.png',
  './static/shirt_main/1.png',
  './static/shirt_main/2.png',
  './static/shirt_main/3.png',
  './static/shirt_main/4.png',
  './static/shirt_number/1.png',
  './static/shirt_number/2.png',
  './static/shirt_number/3.png',
  './static/shirt_number/4.png',
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
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
