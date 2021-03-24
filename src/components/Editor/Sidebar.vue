<template>
  <div>
    <b-button
      v-b-toggle.sidebar-1
      @click="open = !open"
      size="sm"
      variant="dark"
      class="boton_flotante px-4"
      :style="open ? 'left: 23em' : 'left: 1em'"
      v-b-popover.hover.right="open ? 'Cerrar menu' : 'Abrir menu'"
      ><i class="fas" :class="open ? 'fa-arrow-left' : 'fa-arrow-right'"></i
    ></b-button>

    <b-sidebar
      id="sidebar-1"
      shadow
      no-header
      no-close-on-esc
      no-close-on-backdrop
      no-enforce-focus
      no-header-close
      bg-variant="dark"
      class="text-white"
    >
      <div class="px-3 py-2 mt-4">
        <h3 class="text-primary"><b>Creador Web</b></h3>
        <small class="text-success"
          >Elige los elementos que va a tener tu sitio web</small
        >

        <b-row class="mt-3 pl-3">
          <!-- nav -->
          <b-col cols="12" class="my-3 text-left">
            <h4 class="text-left text-white">
              <b>Navbar</b>
            </h4>
            <el-select
              v-model="headerValue"
              clearable
              placeholder="Seleciona tipo de header"
              class="w-100"
              size="small"
              @change="changeSelect(headerValue, 'header')"
            >
              <el-option
                v-for="item in optionsHeader"
                :key="item.tipo"
                :label="item.texto"
                :value="item.tipo"
              >
              </el-option>
            </el-select>
          </b-col>

          <!-- main -->
          <b-col cols="12" class="my-3 text-left" v-if="mostrar_main">
            <h4 class="text-left text-white">
              <b>Main</b>
            </h4>
            <el-select
              v-model="mainValue"
              clearable
              placeholder="Seleciona main"
              class="w-100"
              size="small"
              @change="changeSelect(mainValue, 'main')"
            >
              <el-option
                v-for="item in optionsMain"
                :key="item.tipo"
                :label="item.texto"
                :value="item.tipo"
              >
              </el-option>
            </el-select>
          </b-col>

          <!-- servicios -->
          <b-col cols="12" class="my-3 text-left" v-if="mostrar_service">
            <h4 class="text-left text-white">
              <b>Servicios</b>
            </h4>
            <el-select
              v-model="servicioValue"
              clearable
              class="w-100"
              size="small"
              @change="changeSelect(servicioValue, 'servicio')"
            >
              <el-option
                v-for="item in optionsServicio"
                :key="item.tipo"
                :label="item.texto"
                :value="item.tipo"
              >
              </el-option>
            </el-select>
          </b-col>

          <!-- productos -->
          <b-col cols="12" class="my-3 text-left" v-if="mostrar_productos">
            <h4 class="text-left text-white">
              <b>Productos</b>
            </h4>
            <el-select
              v-model="productosValue"
              clearable
              class="w-100"
              size="small"
              @change="changeSelect(productosValue, 'producto')"
            >
              <el-option
                v-for="item in optionsProductos"
                :key="item.tipo"
                :label="item.texto"
                :value="item.tipo"
              >
              </el-option>
            </el-select>
          </b-col>
        </b-row>

        <div class="mt-2">
          <b-button variant="light" size="sm" class="py-1 px-3" @click="siguiente"
            >Siguiente</b-button
          >
        </div>
      </div>
    </b-sidebar>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  components: {},
  data() {
    return {
      componentes: [
        {
          headerValue: { tipo: "nav-complejo" },
          optionsHeader: [
            { from: "nav", tipo: "nav-complejo", texto: "Navbar Complejo" },
            { from: "nav", tipo: "nav-simple", texto: "Navbar Simple" },
          ],
        },
      ],

      mostrar_main: false,
      mainValue: { tipo: "foto-text" },
      optionsMain: [
        { from: "main", tipo: "foto-text", texto: "Foto y texto" },
        { from: "main", tipo: "fondo_texto", texto: "Fondo y Texto" },
      ],

      mostrar_service: false,
      servicioValue: { tipo: "contenido" },
      optionsServicio: [
        { from: "servicio", tipo: "tarjetas", texto: "Tarjetas" },
        { from: "servicio", tipo: "contenido", texto: "Contenido" },
      ],

      mostrar_productos: false,
      productosValue: { tipo: "productos1" },
      optionsProductos: [
        { from: "producto", tipo: "productos1", texto: "Productos One" },
        { from: "producto", tipo: "productos2", texto: "Productos Two" },
      ],

      open: false,

      count: 3,
    };
  },
  created() {
    this.siguiente();

    this.changeSelect();
    // this.changeMain(this.mainValue.tipo);
    // this.changeServicio(this.servicioValue.tipo);
    // this.changeProductos(this.productosValue.tipo);
  },
  methods: {
    changeSelect(data, tipo) {
      switch (tipo) {
        case "header":
          this.$emit("emitirNavbar", data);
          break;
        case "main":
          this.$emit("emitirMain", data);
          break;
        case "servicio":
          this.$emit("emitirServicio", data);
          break;
        case "producto":
          this.$emit("emitirProducto", data);
          break;

        default:
          break;
      }
      console.log(data, tipo);
    },

    siguiente() {
      this.count++;
      this.count > 1
        ? this.mostrar_main === false
          ? (this.mostrar_main = true)
          : ""
        : "";
      this.count > 2
        ? this.mostrar_service === false
          ? (this.mostrar_service = true)
          : ""
        : "";
      this.count > 3
        ? this.mostrar_productos === false
          ? (this.mostrar_productos = true)
          : ""
        : "";
    },
  },
};
</script>

<style lang="scss" scoped>
.boton_flotante {
  position: fixed;
  top: 25em;
  left: 1em;
}
</style>
