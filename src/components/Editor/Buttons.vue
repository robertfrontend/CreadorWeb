<template>
  <div>
    {{ data }}
    <b-row>
      <b-col cols="auto">
        <b-button variant="outline-primary" size="sm" @click="clickButton(data.funcion)">
          {{ data.texto }}
        </b-button>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "ButtonNavbar",
  props: {
    data: Object,
  },

  methods: {
    clickButton(data) {
      this.$emit('clickButton', data)
    },
  },
};
</script>

<style lang="scss" scoped></style>
