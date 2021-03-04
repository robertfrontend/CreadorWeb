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
      <b-col cols="12">

        <NavbarComplejo v-if="datosNavbar == 'nav-complejo'" />
        <NavbarSimple v-if="datosNavbar == 'nav-simple'" />


        <Main :tipo="datosMain" />

        <Servicios :tipo="datosServicios.tipo" />
        <Productos :tipo="datosProductos.tipo" />
      </b-col>
    </b-row>

    <Sidebar
      @emitirNavbar="emitirNavbar"
      @emitirMain="emitirMain"
      @emitirServicio="emitirServicio"
      @emitirProducto="emitirProducto"
    />

    <div>
      Navbar: <br />
      {{ datosNavbar }}
    </div>
    <br />
    <div>
      Main: <br />
      {{ datosMain }}
    </div>
    <br />
    <div>
      Servicios: <br />
      {{ datosServicios }}
    </div>
    <br />
  </div>
</template>

<script>
import Sidebar from "@/components/Sidebar.vue";

import NavbarComplejo from "@/components/ComponentesConstructores/NavbarComplejo.vue";
import NavbarSimple from "@/components/ComponentesConstructores/NavbarSimple.vue";

import Main from "@/components/ComponentesConstructores/Main/Main.vue";
import Servicios from "@/components/ComponentesConstructores/Servicios/Servicios.vue";
import Productos from "@/components/ComponentesConstructores/Productos/Productos.vue";

export default {
  name: "vista_creador",
  components: {
    Sidebar,
    NavbarComplejo,
    NavbarSimple,
    Main,
    Servicios,
    Productos,
  },
  data() {
    return {
      datosNavbar: "",
      datosMain: "",
      datosServicios: "",
      datosProductos: "",
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
  },
};
</script>

<style lang="scss" scoped>
.layout {
  overflow-x: hidden !important;
}
</style>
