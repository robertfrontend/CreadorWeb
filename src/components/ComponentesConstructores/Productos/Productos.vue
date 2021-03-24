<template>
  <div class="my-5">
    <template v-if="tipo == 'productos1'">
      <b-container>
        <div class="text-center my-4 mb-3">
          <h3><b>Productos</b></h3>
        </div>
        <b-row align-h="center" align-v="center">
          <b-col cols="4" v-for="(producto, index) in productos" :key="index">
            <b-card
              :title="'Producto ' + ++index"
              :img-src="producto.image"
              img-alt="Image"
              img-top
              tag="article"
              class="mb-2"
            >
              <b-card-text>
                Some quick example text to build on the card title and make up.
              </b-card-text>

              <b-button href="#" size="sm" variant="primary">Buy $500</b-button>
            </b-card>
          </b-col>
        </b-row>
      </b-container>
    </template>
    <template v-if="tipo == 'productos2'">
      <b-container>
        <b-row align-v="center" align-h="center">
          <b-col md="6" class="text-left">
            <h4><b>Esto es un subtitulo.</b></h4>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Adipisci veritatis dignissimos accusantium sed vel eos?</p>
            <p class="m-0"><i class="far fa-check-circle mr-1"></i>Lista uno</p>
            <p class="m-0"><i class="far fa-check-circle mr-1"></i>Lista uno</p>
            <p class="m-0"><i class="far fa-check-circle mr-1"></i>Lista uno</p>
          </b-col>
          <b-col md="6">
            <img
              src="https://cdn.pixabay.com/photo/2014/09/07/21/52/city-438393_960_720.jpg"
              width="100%"
              alt=""
              style="border-radius: 10px"
            />
          </b-col>
        </b-row>
      </b-container>
    </template>
  </div>
</template>

<script>
export default {
  name: "Productos",
  props: {
    tipo: String,
  },
  data() {
    return {
      productos: [
        {
          image:
            "https://cdn.pixabay.com/photo/2017/09/17/22/01/pretzel-2759994_960_720.jpg",
        },
        {
          image:
            "https://cdn.pixabay.com/photo/2016/11/29/09/00/abundance-1868573_960_720.jpg",
        },
        {
          image:
            "https://cdn.pixabay.com/photo/2015/11/19/20/17/cookies-1051884_960_720.jpg",
        },
        {
          image:
            "https://cdn.pixabay.com/photo/2017/09/17/22/01/pretzel-2759994_960_720.jpg",
        },
        {
          image:
            "https://cdn.pixabay.com/photo/2016/11/29/09/00/abundance-1868573_960_720.jpg",
        },
        {
          image:
            "https://cdn.pixabay.com/photo/2015/11/19/20/17/cookies-1051884_960_720.jpg",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped></style>
