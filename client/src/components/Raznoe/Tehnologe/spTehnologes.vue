<template>
  <div class="row justify-center">
    <!-- <div class="col-12 col-md-10 row justify-lg-start"> -->

    <!-- <transition name="tehnologes" v-if="tehnologes != null"> -->
    <div class="col-12 col-md-11 col-lg-10 row justify-center q-mt-lg">
      <!-- <transition-group name="vry90" appear> -->
      <q-card class="tehnologe_single col-xs-12 col-sm-3 col-md-2 q-ma-sm" square flat bordered v-for="(tehnologe, index) in tehnologes" :key="index">
        <q-card-section class="a-side column justify-between">
          <q-card-section class="">
            <q-img class="miniatura_tehnologe" no-spinner :src="tehnologe._embedded['wp:featuredmedia']['0'].source_url" fit="contain" />
          </q-card-section>
          <q-separator inset />
          <q-card-section class="title_tehnologe" v-html="tehnologe.title.rendered" />
        </q-card-section>
        <q-card-section class="b-side" v-html="tehnologe.content.rendered" />
      </q-card>
      <!-- </transition-group> -->
    </div>
    <!-- </div> -->
  </div>
</template>

<script>
//import axios from 'axios';
import { ref } from 'vue';
import server from './server';
//import imagesService from './imagesService.vue';

export default {
  setup() {
    const tehnologes = ref([]);

    return {
      tehnologes,
    };
  },

  data() {
    return {};
  },

  methods: {
    // get_miniature_news(id) {
    //   let response_miniature = server.get(`wp/v2/media/${id}`);
    //   console.log(response_miniature.data);
    //   return {
    //     response_miniature,
    //   };
    // },
  },
  components: {},
  async created() {
    let response = await server.get('wp/v2/tehnologe?per_page=20&_embed');
    this.tehnologes = response.data;
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.tehnologe_single {
  text-align: center;
  min-width: 250px;
  height: 400px;
}

.miniatura_tehnologe {
  border: 0px solid red;
  width: 150px;
  margin-top: 20px;
}
.title_tehnologe {
  border: 0px solid red;
  font-size: 18px;
  border: 0px solid red;
  margin-bottom: 50px;
}

.a-side {
  cursor: pointer;

  height: 400px;
}
.b-side {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 400px;
  border: 0px solid red;
  background-color: #fff;
  color: #000;
  opacity: 0;

  transition: all 0.3s;
  cursor: pointer;
}
.b-side:hover {
  opacity: 0.9;
}
/* .vry90-enter-active,
.vry90-leave-active {
  transition: all 500 ease;
}

.vry90-enter-from,
.vry90-leave-to {
  opacity: 0;
} */
</style>
