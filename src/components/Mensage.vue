<template>
  <v-alert v-model="show" dense text type="success">
    <strong>Tempo concluido</strong> click em reset para recomeçar
  </v-alert>
</template>

<script>
export default {
  props: {
    typeAlert: {
      type: String,
    },
    show: {
      type: Boolean,
    },
  },
  data: () => {
    return {
      notifications: [
        "<strong>Tempo concluido</strong> click em reset para recomeçar",
        "<strong>Tempo pausado</strong> click em start para recomeçar",
      ],
      sound: true,
      widgets: false,
    };
  },
};
</script>
