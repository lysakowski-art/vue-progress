<template>
  <div class="progress__bar__wrapper">
    <h3>Weekly Total</h3>
    <div class="progress__bar__container">
      <div class="progress__fill" :style="styles" />
      <div class="progress__value__container">
        <FireSvg size="32" />
        <div class="bar__value">
          {{ Math.round(progress) }}
          <span>%</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FireSvg from "./Fire.vue";
export default {
  name: "ProgressBar",
  components: {
    FireSvg,
  },
  props: {
    value: {
      required: true,
      type: Number,
    },
  },
  computed: {
    styles() {
      return {
        width: `${this.value}%`,
      };
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

<style>
.progress__bar__wrapper {
  width: 95%;
  padding: 10px;
  text-align: center;
}
.progress__bar__wrapper h3 {
  text-align: left;
  font-weight: 600;
  font-size: 14px;
  margin:0;
  margin-bottom:12px;
}

.progress__bar__container {
  width: 100%;
  display: flex;
  align-items: center;
  position: relative;
}
.progress__fill {
  background-color: #dfca8b;
  height: 8px;
  transition: 0.6s all linear;
  border-radius: 5px;
  position: relative;
}
.progress__bar__container::before {
  content: "";
  left: 0;
  right: 0;
  border-radius: 5px;
  position: absolute;
  height: 8px;
  background-color: #ebebeb;
}
.progress__value__container {
  display: flex;
  margin-left: -13px;
  color:#dfca8b;
}
.bar__value {
  position: relative;
  font-size: 18px;
  margin-top: -12px;
  font-weight: 900;
  position: relative;
}
.bar__value span {
  font-size: 12px;
  position: absolute;
  font-weight: 900;
}
</style>
