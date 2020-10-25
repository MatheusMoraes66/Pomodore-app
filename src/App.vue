<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row>
          <v-col>
            <v-btn
              @click="closeDialog()"
              color="secondary"
              small
              absolute
              top
              right
              fab
            >
              <span class="material-icons">
                tune
              </span>
            </v-btn>
            <Pomodoro :dialog="dialog" :closeDialog="closeDialog" />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Pomodoro from "./components/Pomodoro";

export default {
  name: "App",

  components: {
    Pomodoro,
  },

  data: () => {
    return {
      dialog: false,
    };
  },
  methods: {
    closeDialog() {
      this.dialog = !this.dialog;
    },
  },
};
</script>

<style lang="sass" scoped>
.v-main
  margin: 25px auto
</style>
