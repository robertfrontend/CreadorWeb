<template>
  <div class="layout">
    <b-row>
      <b-col cols="2" v-if="false">
        <div class="bg-primary sidebar w-100">
          <h3 class="text-primary"><b>Creador Web</b></h3>
          <small class="text-success"
            >Elige los elementos que va a tener tu sitio web</small
          >
        </div>
      </b-col>
    </b-row>

    <div class="bienvenida" v-if="bienvenida" @click="empezar">
      <div class="cursor">
        <i class="fas fa-mouse-pointer mx-2"></i><i class="fas fa-palette mx-2"></i>
      </div>
      <h4>Bienvenidos a <span>Creador Web</span></h4>
      <br />
      <h5>Dame click para empezar a crear tu pagina web</h5>
    </div>

    <NavbarComplejo v-if="datosNavbar == 'nav-complejo'" />
    <NavbarSimple v-if="datosNavbar == 'nav-simple'" />

    <Main :tipo="datosMain" />

    <Servicios :tipo="datosServicios" />

    <Productos :tipo="datosProductos" />

    <Footer />

    <Sidebar
      @emitirNavbar="emitirNavbar"
      @emitirMain="emitirMain"
      @emitirServicio="emitirServicio"
      @emitirProducto="emitirProducto"
    />

  </div>
</template>

<script>
import Servicios from "@/components/ComponentesConstructores/Servicios/Servicios.vue";
import NavbarComplejo from "@/components/ComponentesConstructores/NavbarComplejo.vue";
import Productos from "@/components/ComponentesConstructores/Productos/Productos.vue";
import NavbarSimple from "@/components/ComponentesConstructores/NavbarSimple.vue";
import Footer from "@/components/ComponentesConstructores/footer/Footer.vue";
import Main from "@/components/ComponentesConstructores/Main/Main.vue";
import Sidebar from "@/components/Sidebar.vue";

export default {
  name: "vista_creador",
  components: {
    Sidebar,
    NavbarComplejo,
    NavbarSimple,
    Main,
    Servicios,
    Productos,

    Footer,
  },
  data() {
    return {
      datosNavbar: "",
      datosMain: "",
      datosServicios: "",
      datosProductos: "",

      bienvenida: true,
    };
  },
  methods: {
    emitirNavbar(data) {
      this.datosNavbar = data;
    },
    emitirMain(data) {
      this.datosMain = data;
    },
    emitirServicio(data) {
      this.datosServicios = data;
    },
    emitirProducto(data) {
      this.datosProductos = data;
    },

    openSidebar() {
      let sidebar, contenido;
      console.log(contenido);
      sidebar = document.querySelector(".sidebar");
      console.log(sidebar);
    },

    empezar() {
      this.emitirNavbar("nav-complejo");
      this.emitirMain("foto-text");
      this.emitirServicio("tarjetas");
      this.emitirProducto("productos2");
      this.bienvenida = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.layout {
  overflow-x: hidden !important;
}
.bienvenida {
  width: 100%;
  height: 100vh;
  position: fixed;
  bottom: auto;
  background: rgb(224, 224, 224);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  span {
    color: #6c63ff;
  }

  .cursor {
    font-size: 5em;
  }
}
</style>
