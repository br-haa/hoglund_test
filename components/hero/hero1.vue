<template>
  <div id="hero">
    <div id="heroBackgroundHolder">
      <slot name="background"></slot>
    </div>
    <div
      id="leftText"
      :style="{
        background: `hsla(${accent.h},${accent.s}%,${accent.l}%,${0.7})`,
      }"
    >
      <slot name="leftText"> </slot>
    </div>
    <div
      id="heroText"
      :style="{
        background: `linear-gradient(to right, hsl(${hsl.h},${hsl.s}%,${
          hsl.l
        }%), hsl(${hsl.h},${hsl.s}%,${hsl.l - 10}%))`,
      }"
    >
      <slot name="text"> </slot>
    </div>
    <div id="hookHolder">
      <slot name="hook"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hero1',
  props: {
    theme: {
      type: Object,
    },
  },
  computed: {
    hsl() {
      const { h, s, l } = this.theme.hsla
      return { h, s, l }
    },
    accent() {
      const { h, s, l } = this.theme.accent
      return { h, s, l }
    },
  },
}
</script>

<style scoped lang="scss">
#hero {
  display: grid;
  width: 100%;
  height: 90vh;
  box-sizing: border-box;
  padding: 100px 0 0 0;
  @media (max-width: 1080px) {
    height: 90vh;
    padding: 200px 0 0 0;
  }
  #heroBackgroundHolder {
    z-index: -1;
    grid-area: 1/1/1/1;
    .background {
      width: 100%;
      height: 80vh;
      object-fit: cover;
      @media (max-width: 1080px) {
        height: 65%;
      }
    }
    .backgroundLight {
      width: 100%;
      height: 80vh;
      object-fit: cover;
      width: 50%;
      object-position: 20% 30%;
    }
    @media (max-width: 1080px) {
      height: 65vh;
      .background {
        object-position: 10% 80% !important;
      }
      .backgroundLight {
        width: 100%;
        object-position: 100% -130px;
      }
    }
  }
  #leftText {
    grid-area: 1/1/1/1;
    justify-self: start;
    z-index: 100;
    align-self: end;
    margin: 0 0 6rem 0;
    width: 50%;
    div {
      text-align: center;
    }
    @media (max-width: 1080px) {
      place-self: center;
      margin: 0 0 4rem 0;
      width: 100%;
    }
  }
  #heroText {
    grid-area: 1/1/1/1;
    height: 100%;
    width: 50%;
    justify-self: end;
    padding: 2rem;
    box-sizing: border-box;
    box-shadow: 0 0 5px 3px black;
    display: grid;
    align-items: center;
    #heroTextGroup {
      margin-top: -7rem;
      #blerb {
        max-width: 500px;
        font-size: clamp(1.3rem, 10 * 1vw / 2.4, 3rem);
        font-weight: 800;
        text-decoration: underline;
      }
    }
    @media (max-width: 1080px) {
      align-items: start;
      align-self: end;
      height: 50%;
      width: 100%;
      #heroTextGroup {
        margin-top: -1rem !important;
      }
      h1 {
        font-size: 1.8rem;
      }
    }
  }
  #heroFormHolder {
    grid-area: 1/1/1/1;
    justify-self: end;
    align-self: center;
    width: 22%;
    margin-right: 5%;
    background: black;
    box-sizing: border-box;
    padding: 1rem;
    border-radius: 10px;
    @media (max-width: 1080px) {
      align-self: end;
      width: 100%;
      margin-right: 0;
      justify-self: center;
    }
  }
  #hookHolder {
    grid-area: 1/1/1/1;
    align-self: end;
    justify-self: center;
    margin-bottom: -2rem;
    max-width: 300px;
  }
}
</style>
<style lang="scss">
#form-inside {
  .consent-text {
    font-size: 0.8rem !important;
  }
  .buttonGrid {
    margin-top: 0.5rem !important;
  }
  #Message {
    height: 100px;
  }
  #formTopText {
    margin: 0;
    @media (max-width: 640px) {
      font-size: 1.5rem;
    }
  }
  #formBotText {
    margin: 0;
    @media (max-width: 640px) {
      font-size: 3rem;
    }
  }
}
</style>
