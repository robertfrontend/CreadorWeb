<template>
  <div style="z-index: 10000" class="my-2">
    <div class="botonEdit text-white cursor-pointer text-center">
      <i class="fas fa-pencil-alt p-2" @click="openEdit = !openEdit"></i>
    </div>

    <div class="editComponent text-dark p-3 text-center bg-light" v-if="openEdit">
      <p><b>Editar</b></p>

      <template v-if="componentes.fondo">
        <b-row class="w-100 my-2" align-h="center" align-v="center">
          <b-col cols="12"
            ><p class="m-0 pb-2">
              <b><slot name="tituloFondo">Cambiar fondo:</slot></b>
            </p></b-col
          >
          <b-col
            cols="1"
            class="mx-1"
            v-for="(bg, index) in componentes.backgrounds"
            :key="index"
          >
            <div
              class="spanColor my-1"
              :class="selecionado === index ? 'selecionado' : ''"
              :style="'background:' + bg.color"
              :key="index"
              @click="botonBackground(bg, index, 'fondo')"
            ></div>
          </b-col>
        </b-row>
      </template>

      <template v-if="componentes.colores">
        <b-row class="w-100 my-2" align-h="center" align-v="center">
          <b-col cols="12"
            ><p class="m-0 pb-2">
              <b><slot name="tituloColor">Cambiar Color:</slot></b>
            </p></b-col
          >
          <b-col
            cols="1"
            class="mx-1"
            v-for="(bg, index) in componentes.coloresText"
            :key="index"
          >
            <div
              class="spanColor my-1"
              :class="selecionadoTextColor === index ? 'selecionado' : ''"
              :style="'background:' + bg.color"
              :key="index"
              @click="botonTextColor(bg, index, 'colorText')"
            ></div>
          </b-col>
        </b-row>
      </template>
    </div>
  </div>
</template>
<script>
/**
  *! prop obligatorio
  @param componentes // este props es obligatorio 
   @param fondo // bloean props - variable para mostrar el cambio de color de fondo
    @param backgrounds // objeto - props sirve para agregarle los colores de los botones
*/

export default {
  name: "EditComponent",
  props: {
    componentes: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      colors: [
        { color: "gray", id: "black" },
        { color: "#3498db", id: "blue" },
        { color: "#2ecc71", id: "green" },
      ],

      openEdit: false,

      selecionado: null,
      selecionadoTextColor: null,
    };
  },
  methods: {
    botonBackground(color, index) {
      this.$emit("eventoColor", color);
      this.selecionado = index;
    },

    botonTextColor(color, index) {
      this.$emit("eventoColorText", color);
      this.selecionadoTextColor = index;
    },
  },
};
</script>

<style lang="scss" scoped>
.botonEdit {
  width: auto;
  padding: 10px 0;
  i {
    background: rgba(3, 135, 212, 0.918);
    color: white;
    font-size: 20px;
    border-radius: 20px;
  }
}

.editComponent {
  width: 100%;
  border-radius: 10px;
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.267);
}
.spanColor {
  width: 30px;
  height: 30px;
  border-radius: 25px;
  cursor: pointer;
  border: 3px solid transparent;
  transition: all 0.2s;
}

.selecionado {
  transition: all 0.2s;
  border: 3px solid #e74c3c;
}
</style>
