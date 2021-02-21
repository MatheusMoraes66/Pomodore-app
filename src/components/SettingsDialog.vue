<template>
  <v-row justify="center">
    <v-dialog
      v-model="dialog"
      fullscreen
      hide-overlay
      transition="dialog-bottom-transition"
    >
      <v-card>
        <v-toolbar dark>
          <v-btn icon dark @click="closeDialog">
            <v-icon>close</v-icon>
          </v-btn>
          <v-toolbar-title>Settings Timer</v-toolbar-title>
          <v-spacer></v-spacer>
        </v-toolbar>

        <v-divider> </v-divider>
        <div class="settings-conteiner">
          <v-row>
            <v-col>
              <div class="timer-settings">
                <h3>Timer Pomodoro</h3>
                <v-slider
                  v-model="fruits"
                  :tick-labels="ticksLabels"
                  :max="11"
                  step="1"
                  ticks="always"
                  tick-size="8"
                  :thumb-size="24"
                  thumb-label="always"
                >
                  <template v-slot:thumb-label="{}"> </template>
                </v-slider>
              </div>
              <div class="timer-settings">
                <h3>Timer Short Break</h3>
                <v-slider
                  v-model="fruits"
                  :tick-labels="ticksLabels"
                  :max="11"
                  step="1"
                  ticks="always"
                  tick-size="8"
                  :thumb-size="24"
                  thumb-label="always"
                >
                  <template v-slot:thumb-label="{}"> </template>
                </v-slider>
              </div>
              <div class="timer-settings">
                <h3>Timer Long Break</h3>
                <v-slider
                  v-model="fruits"
                  :tick-labels="ticksLabels"
                  :max="11"
                  step="1"
                  ticks="always"
                  tick-size="8"
                  :thumb-size="24"
                  thumb-label="always"
                >
                  <template v-slot:thumb-label="{}"> </template>
                </v-slider>
              </div>

              <v-switch
                v-model="darkmode"
                inset
                :label="`Dark Mode`"
              ></v-switch>
            </v-col>
          </v-row>
        </div>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>
export default {
  props: {
    dialog: {
      type: Boolean,
    },
    closeDialog: {
      type: Function,
      required: true,
    },
    save: {
      type: Function,
      required: true,
    },
  },
  data: () => {
    return {
      ticksLabels: [
        "05:00",
        "10:00",
        "15:00",
        "20:00",
        "25:00",
        "30:00",
        "35:00",
        "40:00",
        "45:00",
        "50:00",
        "55:00",
        "60:00",
      ],
      darkmode: false,
      sound: true,
      widgets: false,
    };
  },
};
</script>

<style lang="sass" scoped>
.settings-conteiner
  margin: 20px 50px

.timer-settings
  margin: 20px auto

.timer-settings h3
  padding: 30px 10px

@media (max-width: 768px)
  .settings-conteiner
    margin: 20px 10px
</style>
