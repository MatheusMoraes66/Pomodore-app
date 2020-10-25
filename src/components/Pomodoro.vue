<template>
  <v-card>
    <v-tabs
      @change="changeCurrentTimer"
      v-model="currentTimer"
      background-color="transparent"
      grow
      center-active
    >
      <v-tab v-for="tabTimer in tabsTimers" :key="tabTimer">
        {{ tabTimer.name }}
      </v-tab>
    </v-tabs>

    <v-card class="pa-5" v-model="currentTimer" flat>
      <h1 class="time">{{ displayMinutes }}:{{ displaySeconds }}</h1>
      <div class="d-flex justify-space-around">
        <v-btn depressed @click="start()" color="success">
          <span class="material-icons">
            play_arrow
          </span>
          Start
        </v-btn>
        <v-btn depressed @click="stop()" color="error">
          <span class="material-icons">
            stop
          </span>
          Stop
        </v-btn>
        <v-btn
          depressed
          :disabled="this.paused == false"
          @click="restart(tabsTimers[currentTimer].minutes)"
        >
          <span class="material-icons">
            replay
          </span>
          Reset
        </v-btn>
      </div>
    </v-card>
    <SettingsDialog :dialog="dialog" :closeDialog="closeDialog" :save="save" />
  </v-card>
</template>

<script>
import SettingsDialog from "./SettingsDialog.vue";
import "material-design-icons-iconfont/dist/material-design-icons.css";

export default {
  components: {
    SettingsDialog,
  },
  props: {
    dialog: {
      type: Boolean,
      required: true,
    },
    closeDialog: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      keyInterval: null,
      paused: true,
      totalSeconds: 25 * 60,
      currentTimer: 0,
      tabsTimers: [
        {
          name: "Pomodoro",
          minutes: 25,
        },
        {
          name: "Short Break",
          minutes: 5,
        },
        {
          name: "Long Break",
          minutes: 60,
        },
      ],
    };
  },
  computed: {
    displayMinutes() {
      const minutes = Math.floor(this.totalSeconds / 60);
      return this.formatTime(minutes);
    },
    displaySeconds() {
      const seconds = this.totalSeconds % 60;

      return this.formatTime(seconds);
    },
  },
  methods: {
    formatTime(time) {
      if (time < 10) {
        return "0" + time;
      } else {
        return time.toString();
      }
    },
    start() {
      this.paused = false;
      this.keyInterval = setInterval(() => {
        if (this.paused === false) {
          this.totalSeconds -= 1;
        }
      }, 1000);
    },
    stop() {
      clearInterval(this.keyInterval);
      this.paused = !this.paused;
    },
    restart(minutes) {
      clearInterval(this.keyInterval);
      this.totalSeconds = minutes * 60;
    },
    changeCurrentTimer(num) {
      this.currentTimer = num;
      this.restart(this.tabsTimers[num].minutes);
    },
    save() {
      this.closeDialog;
    },
  },
};
</script>

<style lang="sass" scoped>
.v-card
  max-width: 600px

.time
    font-size: 100px
    font-weight: 500
    text-align: center

@media (max-width: 768px)
  .v-tab
    font-size: 10px
    font-weight: 800
</style>
