<template>
  <div class="my-5">

    <template v-if="tipo == 'tarjetas'">
      <b-container>
        <b-row align-h="center" align-v="center">
          <b-col cols="12" class="text-center">
            <EditComponent
              class="mx-auto"
              style="width: 350px"
              @eventoColor="eventoColor"
              :componentes="{
                fondo: true,
                colores: false,
                backgrounds: background,
              }"
            >
              <template #tituloFondo> Cambiar el color de los iconos </template>
            </EditComponent>
          </b-col>
          <b-col lg="4" class="my-2 text-center" v-for="(tarjeta, index) in tarjetas" :key="index">
            <b-card
              no-body
              class="overflow-hidden mx-auto"
              style="max-width: 340px"
              :style="'background:' + color_icono"
              :class="`${color_icono != '' ? 'text-white' : ''}`"
            >
              <b-row no-gutters>
                <b-col md="12" class="mt-4">
                  <i class="fas fa-store" style="font-size: 3em"></i>
                </b-col>
                <b-col md="12">
                  <b-card-body>
                    <h4 contenteditable="">Horizontal Card</h4>
                    <b-card-text contenteditable="">
                      This is a wider card with supporting text as a natural lead-in to
                      additional content. This content is a little bit longer.
                    </b-card-text>
                  </b-card-body>
                </b-col>
              </b-row>
            </b-card>
          </b-col>
        </b-row>
      </b-container>
    </template>

    <template v-if="tipo == 'contenido'">
      <b-container>
        <b-row align-v="center" align-h="center">
          <b-col md="4">
            <img
              src="https://cdn.pixabay.com/photo/2014/09/07/21/52/city-438393_960_720.jpg"
              width="100%"
              alt=""
            />
          </b-col>
          <b-col md="8" class="text-left">
            <h4><b>Esto es un subtitulo.</b></h4>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum cupiditate,
              temporibus sed odit nesciunt fugit quaerat quibusdam voluptatum iure
              explicabo.
            </p>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nemo, animi!</p>
          </b-col>
        </b-row>
      </b-container>
    </template>
  </div>
</template>

<script>
export default {
  name: "Tarjetas",
  props: {
    tipo: String,
  },
  data() {
    return {
      tarjetas: [1, 2, 3],
      loading: false,

      background: [
        { color: "#2c3e50", id: "black" },
        { color: "#3498db", id: "blue" },
        { color: "#2ecc71", id: "green" },
        { color: "rgba(34, 0, 185, 0.719)", id: "navy" },
      ],

      // changes
      selecionado: null,
      color_icono: "",
    };
  },
  watch: {
    tipo() {
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
      }, 1000);
    },
  },
  methods: {
    eventoColor(color) {
      this.color_icono = color.color;
      console.log({ color });
    },
    selectIcono(selectIcono) {
      console.log({ selectIcono });
      this.selecionado = selectIcono;
    },
  },
};
</script>

<style lang="scss" scoped></style>
