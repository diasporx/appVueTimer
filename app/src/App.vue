<template>
  <section>
        <Timer />
  </section>
</template>

<script>
import Timer from './components/Timer.vue'

export default {
  name: 'App',
  components: {
    Timer
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

@font-face {
  font-family: 'Gotham';
  src: url(./assets/font/gothampro_bold.ttf);
  font-weight: 700;
}
@font-face {
  font-family: 'Gotham';
  src: url(./assets/font/gothampro_medium.ttf);
  font-weight: 400;
}
@font-face {
  font-family: 'Gotham';
  src: url(./assets/font/gothampro_light.ttf);
  font-weight: 300;
}

body {
  background: #353638;
  min-height: 100vh;
}
</style>
