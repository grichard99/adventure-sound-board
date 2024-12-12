<template>
  <div class="flex items-center justify-center w-5/8 h-5/8">
    <div class="svg-container">
      <div id="outerWrapper" class="ghosted">
        <svg
          class="lightning-container"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          viewBox="-243.6 360 41.6 73.7"
        >
          <defs>
            <path
              id="SVGID_1_"
              class="stroke"
              d="M-202.4 362.5c.6-1 .3-1.7-.5-2.2-.7-.4-1.6-.3-2.2.7l-30.9 38.2c-.1.1-.1.1-.1.2l-.1.1c-.2.3-.2.6-.1.8.1.6.8.8 1.7.9h7.6c1.5-.1 2.2.8 1.6 1.8l-17.3 28.5c-.6 1-.3 1.7.5 2.2.7.4 1.5.2 2.2-.7l30.9-38.2c.1-.1.1-.1.1-.2l.1-.1c.2-.3.2-.6.1-.8-.1-.6-.8-.8-1.7-.9l-7.5-.1c-1.5.1-2.2-.8-1.6-1.8l17.2-28.4"
            />
          </defs>
          <clipPath id="SVGID_2_">
            <use xlink:href="#SVGID_1_" overflow="visible" />
          </clipPath>
          <path
            id="path"
            class="st0 lightning stroke"
            d="M-202.9 360.3L-229 397h13l-26.2 36.5"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
.st0 {
  clip-path: url(#SVGID_2_);
  fill: none;
}
@keyframes full {
  0% {
    opacity: 0;
    stroke-dashoffset: 0;
  }
  /* 1 */
  3.33% {
    opacity: 0;
    stroke-width: 2;
    stroke-dashoffset: 0;
  }
  /* 2 */
  6.66% {
    opacity: 0;
    stroke-width: 2;
    stroke-dashoffset: 0;
  }
  /* 3 */
  9.99% {
    opacity: 0;
    stroke-width: 2;
    stroke-dashoffset: 0;
  }
  /* 4 */
  13.32% {
    opacity: 1;
    stroke-width: 2;
    stroke-dashoffset: 0;
  }
  /* 5 */
  16.65% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /*6*/
  19.98% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /*  7*/
  23.31% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /*8*/
  26.64% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /*9*/
  29.97% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /*10*/
  33.33% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /*11*/
  36.66% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /*12*/
  39.99% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /*13*/
  43.32% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /* 14 */
  46.65% {
    opacity: 1;
    stroke-width: 15;
    stroke-dashoffset: 0;
  }
  /*15*/
  49.98% {
    stroke-width: 7;
    stroke-dashoffset: 0;
  }
  /*16*/
  53.31% {
    stroke-width: 6;
    stroke-dashoffset: 0;
  }
  /*17*/
  56.64% {
    stroke-width: 5;
    stroke-dashoffset: 0;
  }
  /*18*/
  59.97% {
    stroke-width: 4;
  }
  /*19*/
  63.33% {
    stroke-width: 3;
  }
  /*20*/
  66.66% {
    stroke-width: 2;
    opacity: 0.8;
  }
  /*21*/
  69.99% {
    stroke-width: 1;
    opacity: 0.6;
  }
  /*22*/
  73.32% {
    stroke-width: 1;
    opacity: 0.4;
  }
  /*23*/
  76.55% {
    stroke-width: 1;
    opacity: 0.2;
  }
  /*24*/
  79.98% {
    stroke-width: 1;
    opacity: 0;
  }
  /*25*/
  83.31% {
    stroke-width: 1;
    opacity: 0;
  }
  /*26*/
  86.64% {
    stroke-width: 1;
    opacity: 0;
  }
  /*27*/
  89.97% {
    stroke-width: 1;
    opacity: 0;
  }
  /*28*/
  93.33% {
    stroke-width: 1;
    opacity: 0;
  }
  /*29*/
  96.66% {
    stroke-width: 1;
    opacity: 0;
  }
  /*30*/
  100% {
    stroke-width: 1;
    opacity: 0;
    // See js for how to get the number below
    stroke-dashoffset: 102.96427917480469;
  }
}
@keyframes scale {
  0% {
    transform: scale(1);
  }
  /* 4 */
  13.32% {
    transform: scale(1);
  }
  /* 5 */
  16.65% {
    transform: scale(1.2);
  }
  /*  7*/
  23.31% {
    transform: scale(1);
  }
  /*8*/
  100% {
    transform: scale(1);
  }
}
.svg-container {
  width: 100%;
  height: 100%;
  &:before {
    content: "";
    display: inline-block;
    vertical-align: middle;
    height: 100%;
    margin-right: -0.25em;
  }
  .ghosted {
    display: inline-block;
    vertical-align: middle;
  }
}
.lightning-container {
  width: 100px;
  transform-origin: 50% 50%;
  animation: scale 1s ease infinite forwards;
}
.lightning {
  stroke: #ef4337;
  stroke-miterlimit: 10;
  fill: #ef4137;
  // See js for how to get the number below
  stroke-dasharray: 102.96427917480469;
  stroke-dashoffset: 0;
  animation: full 1s ease-out infinite forwards;
}
</style>
