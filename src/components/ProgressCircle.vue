<template>
  <div class="skill">
    <div class="outer">
      <div class="inner">
        <div class="container">
          <FireSvg />
          <h3 class="label">{{ label }}</h3>
          <div class="value">{{  Math.round(progress) }}<span class="percent">%</span></div>
        </div>
      </div>
    </div>

    <svg
      xmlns="http://www.w3.org/2000/svg"
      version="1.1"
      width="160px"
      height="160px"
      class="rotate__svg"
    >
      <defs>
        <linearGradient id="GradientColor">
          <stop offset="0%" stop-color="#dfca8b" />
          <stop offset="100%" stop-color="#dfca8b" />
        </linearGradient>
      </defs>
      <circle :style="styles" cx="80" cy="80" r="75" stroke-linecap="round" />
    </svg>
  </div>
</template>

<script>
import FireSvg from "./Fire.vue";
export default {
  name: "ProgressCircle",
  components: {
    FireSvg,
  },
  props: {
    value: {
      required: true,
      type: Number,
      default: 0,
    },
    speed: {
      type: Number,
      default: 0.5,
    },
    label: {
      required: true,
      type: String,
    },
  },
  data() {
    return {
      progress: 0,
      interval: null,
    };
  },
  watch: {
    progress(newProgressValue, oldProgressValue) {
      if (newProgressValue > this.value) {
        this.onStopInterval();
      } else if (oldProgressValue > this.value) {
        console.log(oldProgressValue);
      }
    },
  },
  computed: {
    styles() {
      return {
        "stroke-dashoffset": `${472 - 472 * (this.value / 100)}`,
        transition: `${this.speed}s all linear`,
      };
    },
  },
  mounted() {
    this.onStartInterval();
  },
  methods: {
    onStartInterval() {
      this.iterval = setInterval(this.incrementProgress, 10);
    },
    onStopInterval() {
      clearInterval(this.interval);
    },
    incrementProgress() {
      if (this.value != this.progress) return this.progress++;
    },
  },
};
</script>

<style scoped>
.skill {
  width: 160px;
  height: 160px;
  position: relative;
}

.outer {
  height: 160px;
  width: 160px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ebebeb;
  box-shadow: 6px 6px 10px -1px rgba(0, 0, 0, 0.15),
    6px 6px 10px -1px rgba(255, 255, 255, 0.7);
}

/* padding: 20px; */
.inner {
  height: 140px;
  width: 140px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;

  background: linear-gradient(
    0deg,
    rgba(244, 233, 203, 1) 0%,
    rgba(255, 255, 255, 1) 100%
  );

  box-shadow: inset 4px 4px 6px -1px rgba(0, 0, 0, 0.2),
    inset -4px -4px 6px -1px rgba(255, 255, 255, 0.7),
    -0.5px -0.5px 0px rgba(255, 255, 255, 1),
    0.5px 0.5px 0px rgba(0, 0, 0, 0.15), 0px 12px 10px -10px rgba(0, 0, 0, 0.05);
}
.container {
  margin: auto;
}
.label {
  margin: 0;
  margin-top: 2px;
  font-size: 17px;
  font-weight: bold;
}

.value {
  font-size: 40px;
  font-weight: 900;
  color: #000;
  line-height: 40px;
  position: relative;
}
.percent {
  font-weight: 900;
  top: -10px;
  font-size: 15px;
  position: absolute;
}

circle {
  fill: none;
  stroke: url(#GradientColor);
  stroke-width: 10px;
  stroke-dasharray: 472;
  stroke-dashoffset: 472;
  /* animation: anim */
}
svg {
  position: absolute;
  top: 0;
  left: 0;
}
.rotate__svg{
  transform:rotate(-90deg)
}
</style>
