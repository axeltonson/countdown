<template>
  <svg class="circles" version="1.1" viewBox="0 0 500 500" preserveAspectRatio="xMinYMin meet">
    <circle class="circle circle--1" cx="250" cy="250" r="200"></circle>
    <circle class="circle circle--2" cx="250" cy="250" r="210"></circle>
    <circle class="circle circle--3" cx="250" cy="250" r="190"></circle>
    <circle class="circle circle--4" cx="250" cy="250" r="215"></circle>
  </svg>
</template>

<style lang="scss" scoped>
  .circles {
    position: absolute;
    top: 0;
    left: 50%;
    height: 100%;
    transform: translateX(-50%);
  }
  .circle {
    fill: transparent;
    opacity: 0.1;
    transform-origin: 50% 50%;
  }
  .circle--1 {
    stroke-width: 4px;
    stroke: $white;
    stroke-dasharray: calc(2 * 3.14 * 200 / 6);
    animation: rotation 36s infinite linear;
  }
  .circle--2 {
    stroke-width: 2px;
    stroke: $red;
    stroke-dasharray: calc(2 * 3.14 * 210 / 4);
    animation: rotation 6s reverse infinite linear;
  }
  .circle--3 {
    stroke-width: 2px;
    stroke: $blue;
    stroke-dasharray: calc(2 * 3.14 * 190 / 240);
    animation: rotation 72s infinite linear;
  }
  .circle--4 {
    stroke-width: 2px;
    stroke: $white;
    stroke-dasharray: calc(2 * 3.14 * 215 / 8);
    animation: rotation 36s reverse infinite linear;
  }
  @keyframes rotation {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }
</style>
