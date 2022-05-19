<template>
  <div>
    <div class="main__circular__progress_wrapper">
      <div class="progress__container">
        <ProgressCircle :label="'Mon.'" :value="this.circularPogressValue" />
      </div>
      <div class="progress__container">
        <ProgressCircle
          :label="'Tue.'"
          :value="this.circularPogressValue * 8.1"
        />
      </div>
      <div class="progress__container">
        <!--  -->
        <ProgressCircle
          :label="'Wed.'"
          :value="this.circularPogressValue * 5"
        />
      </div>
      <div class="progress__container">
        <ProgressCircle
          :label="'Thu.'"
          :value="this.circularPogressValue * 5.3"
        />
      </div>
      <div class="progress__container">
        <ProgressCircle
          :label="'Fri.'"
          :value="this.circularPogressValue * 1.2"
        />
      </div>
      <div class="progress__container">
        <ProgressCircle
          :label="'Sat.'"
          :value="this.circularPogressValue * 2.9"
        />
      </div>
      <div class="progress__container">
        <ProgressCircle
          :label="'Sat.'"
          :value="this.circularPogressValue * 10"
        />
      </div>
    </div>
    <ProgressBar :value="this.circularPogressValue *7.8"/>
  </div>
</template>

<script>
import ProgressBar from './ProgressBar.vue';
import ProgressCircle from "./ProgressCircle.vue";

export default {
  name: "NewIndex",
  components: {
    ProgressCircle,ProgressBar
  },
  data() {
    return {
      circularPogressValue: 0,
    };
  },

  mounted() {
    setTimeout(() => (this.circularPogressValue = 10), 2000);
  },
};
</script>

<style scoped>
body {
  margin: 0;
  padding: 0;
}
.main__circular__progress_wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.progress__container{
 padding: 1rem;
}
</style>
