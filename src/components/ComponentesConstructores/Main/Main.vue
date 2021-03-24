<template>
  <div>
    <template v-if="tipo == 'fondo_texto'">
      <div class="bg-dark text-white padre">
        <div class="fondo" :style="'background:' + backgroun_main.color">
          <b-container>
            <b-row align-h="start" align-v="start" class="my-4 py-4">
              <b-col cols="6" class="text-left py-4 py-4">
                <h1 contenteditable="" :style="'color:' + color_main.color">
                  <b>
                    Puedes cambiar este texto si deseas. Tambien el texto de abajo esta
                    disponible.
                  </b>
                </h1>
                <p>
                  Lorem ipsum dolor sit amet consectetur adipisicing elit. Porro, fuga.
                </p>
                <b-button variant="outline-light" class="px-4 "
                  >Click me!</b-button
                >
  
              </b-col>
            </b-row>
          </b-container>
        </div>
      </div>
    </template>

    <template v-if="tipo == 'foto-text'">
      <div class="text-white padre-text py-4" :style="'background:' + backgroun_main.color">
        <b-container>
          <b-row align-h="center" align-v="center" class="py-4">
            <b-col cols="6" class="text-left py-4 py-4">
              <h1 contenteditable="" :style="'color:' + color_main.color"><b>Puedes cambiar este texto si deseas.</b></h1>
              <p>
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Dicta, minus?
              </p>
              <b-button variant="light" class="px-4">Click me!</b-button>
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
        </b-container>
                  <!-- componente editar -->
              <div class="componenteEditar">
                <EditComponent
                  @eventoColor="eventoColor"
                  @eventoColorText="eventoColorText"
                  :componentes="{ 
                    fondo: true, 
                    colores: true,
                    backgrounds: background, 
                    coloresText: coloresText, 
                    }"
                />
              </div>
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

      backgroun_main: "",
      color_main: "",

      background: [
        { color: "#2c3e50", id: "black" },
        { color: "#3498db", id: "blue" },
        { color: "#2ecc71", id: "green" },
        { color: "rgba(34, 0, 185, 0.719)", id: "navy" },
      ],

      coloresText: [
        { color: "#2c3e50", id: "black" },
        { color: "#dfe6e9", id: "cly" },
        { color: "#b2bec3", id: "gray" },
        { color: "#00b894", id: "green" },
      ],
    };
  },

  watch: {
    tipo() {
      if (this.tipo == "fondo_texto") {
        this.backgroun_main = "";
      }
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
      }, 1000);
    },
  },

  methods: {

    eventoColor(color) {
      this.backgroun_main = color;
      this.filtroColores()
    },

    eventoColorText(color) {
      this.color_main = color;
      this.filtroColores()
    },


    filtroColores() {

      if(this.backgroun_main.id ===  this.color_main.id) {
        this.$confirm('El color de fondo y el color del texto son identicos, deseas continuar?', 'Advertencia', {
          confirmButtonText: 'Si',
          cancelButtonText: 'Cacelar',
          type: 'warning'
        }).then(() => {
        }).catch(() => {
          this.backgroun_main = this.background[0]
          this.color_main = this.coloresText[1]
        });
      }
    }

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
.componenteEditar{
  position: absolute;
  top: 10em;
  right: 4em;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-end;
  padding: 0 1em;
}
</style>
