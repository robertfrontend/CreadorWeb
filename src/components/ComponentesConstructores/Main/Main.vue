<template>
  <div>
    <template v-if="loading">
      <b-container class="mt-5">
        <b-row>
          <b-col cols="6">
            <b-skeleton animation="wave" width="100%" height="10vh"></b-skeleton>
            <b-skeleton animation="wave" width="100%"></b-skeleton>
            <b-skeleton animation="wave" width="10%" height="2vh"></b-skeleton>
          </b-col>
          <b-col cols="6">
            <b-skeleton animation="wave" width="100%" height="15vh"></b-skeleton>
          </b-col>
        </b-row>
      </b-container>
    </template>

    <template v-if="tipo == 'fondo_texto' && loading != true">
      <div class="bg-dark text-white padre">
        <div class="fondo" :style="'background:' + color_main">
          <b-container>
            <b-row align-h="start" align-v="start" class="my-4 py-4">
              <b-col cols="6" class="text-left py-4 py-4">
                <h1 contenteditable="">
                  Puedes cambiar este texto si deseas. Tambien el texto de abajo esta
                  disponible.
                </h1>
                <p>
                  Lorem ipsum dolor sit amet consectetur adipisicing elit. Porro, fuga.
                </p>
                <b-button size="sm" variant="outline-light" class="px-4"
                  >Click me!</b-button
                >
              </b-col>
            </b-row>
          </b-container>
        </div>
      </div>
    </template>

    <template v-if="tipo == 'foto-text' && loading != true">
      <div class="text-white padre-text py-4" :style="'background:' + color_main">
        <b-container>
          <b-row align-h="center" align-v="center" class="py-4">
            <b-col cols="6" class="text-left py-4 py-4">
              <h1 contenteditable="">Puedes cambiar este texto si deseas.</h1>
              <p>
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Dicta, minus?
              </p>
              <b-button size="sm" variant="light" class="px-4">Click me!</b-button>
            </b-col>
            <b-col cols="6">
              <img
                width="100%"
                class="image"
                src="https://cdn.pixabay.com/photo/2015/10/12/15/18/store-984393_960_720.jpg"
                alt=""
              />
            </b-col>
          </b-row>

          <!-- componente editar -->
          <b-row align-v="center" align-h="center">
            <b-col md="4">
              <EditComponent
                @eventoColor="eventoColor"
                :componentes="{ 
                fondo: true, 
                colores: false,
                 backgrounds: background }"
              />
            </b-col>
          </b-row>

        </b-container>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "FotoyTexto",
  props: {
    tipo: String,
  },
  components: {},
  data() {
    return {
      loading: false,

      color_main: "",


      background: [
        { color: "#2c3e50", id: "black" },
        { color: "#3498db", id: "blue" },
        { color: "#2ecc71", id: "green" },
        { color: "rgba(34, 0, 185, 0.719)", id: "navy" },
      ],
    };
  },

  watch: {
    tipo() {
      if (this.tipo == "fondo_texto") {
        this.color_main = "";
      }
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
      }, 1000);
    },
  },

  methods: {
    eventoColor(color) {
      this.color_main = color.color;
      console.log({ color });
    },
  },
};
</script>

<style lang="scss" scoped>
.padre {
  background: url("https://cdn.pixabay.com/photo/2015/10/12/15/18/store-984393_960_720.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: right;
  height: 50vh;
}
.fondo {
  width: 100%;
  height: inherit;
  background: rgba(0, 1, 20, 0.719);
  display: flex;
  align-items: center;
  justify-content: center;
}

.padre-text {
  background: rgba(34, 0, 185, 0.719);
  img {
    border-radius: 20px;
  }
}
</style>
