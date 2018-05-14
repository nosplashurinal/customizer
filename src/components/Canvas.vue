<template>
    <canvas ref="canvas" id="canvas" :width="width" :height="height"></canvas>
</template>
<script>
export default {
    name: 'Canvas',
    props: ['width', 'height', 'images'],
    mounted() {
        this.images !== null && this.drawImages()
    },
    beforeUpdate() {
        console.log('here');
        this.images !== null && this.drawImages()
    },
    methods: {
        drawImages: function () {
            const ctx = this.$refs.canvas.getContext('2d');
            ctx.drawImage(this.images[0], 0, 0, 500, 500);
            ctx.drawImage(this.images[4], 0, 0, 500, 500);
            ctx.drawImage(this.images[8], 0, 0, 500, 500);
            ctx.drawImage(this.images[12], 0, 0, 500, 500);
        }
    }
}
</script>
<style lang="scss">
#canvas {
    position: absolute;
    top: 0;
    left: 0;
}
</style>
