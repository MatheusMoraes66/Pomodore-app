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
          <v-toolbar-items>
            <v-btn dark text @click="save">Save</v-btn>
          </v-toolbar-items>
        </v-toolbar>

        <v-divider></v-divider>
        <v-list three-line subheader>
          <v-subheader>User Controls</v-subheader>
        </v-list>
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
      notifications: false,
      sound: true,
      widgets: false,
    };
  },
};
</script>
