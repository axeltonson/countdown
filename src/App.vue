<template>
  <div id="app">
    <h1>Bachelor web
      <span class="subtitle">promotion 2018</span>
    </h1>
    <countdown date='31/08/2018/17/00'/>
  </div>
</template>

<script>
import Countdown from '@/components/Countdown'
export default {
  name: 'App',
  components: {
    Countdown
  }
}
</script>

<style lang="scss">
  html {
    font-size: 16px;
    height: 100vh;
    width: 100vw;
    overflow: hidden;
    @media #{$mobile} {
      font-size: 8px;
    }
  }
  body {
    margin: 0;
    height: 100%;
    overflow: hidden;
  }
  #app {
    background:  radial-gradient(#151E3F, rgb(10, 16, 36));
    font-family: 'Titillium Web', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: $red;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  h1 {
    font-weight: 400;
    text-transform: uppercase;
    font-size: 4rem;
    letter-spacing: 1rem;
    margin: 0 0 50px 0;
    @media #{$mobile} {
      margin: 0;
      font-size: 3.5rem;
    }
  }
  .subtitle {
    display: block;
    font-size: 2rem;
    margin: 0;
    letter-spacing: 1.75rem;
    font-weight: 200;
    transform: translateX(5px);
    @media #{$mobile} {
      margin: 10px 0 0;
    }
  }
</style>
