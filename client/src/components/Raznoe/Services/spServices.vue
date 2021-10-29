<template>
  <div class="row justify-center">
    <transition-group name="vry90" appear>
      <q-card class="col-12 col-md-10 q-ma-md" flat bordered v-for="(service, i) in services" :key="i">
        <q-card-section>
          <q-card-section horizontal class="q-pa-lg">
            <q-card-section class="col-12 col-md-9">
              <div class="title_service">{{ service.title.rendered }}</div>
              <div v-html="service.content.rendered" class="content_service" />
            </q-card-section>
            <q-separator vertical class="gt-sm" />
            <q-card-section class="col-sm-3 flex flex-center q-ma-lg gt-sm">
              <q-img class="rounded-borders type_service_img" :src="service._embedded['wp:featuredmedia']['0'].source_url" fit="contain" no-spinner />
            </q-card-section>
          </q-card-section>
          <q-separator />
          <q-card-section>
            <sp-portfoliotype :id_typeservice="service.type_service_chivic"></sp-portfoliotype>
          </q-card-section>
        </q-card-section>
      </q-card>
    </transition-group>

    <!-- <div v-for="(service, i) in services" :key="i" class="col-12 col-md-10 mmm">
      {{ service.title.rendered }}
      <sp-portfoliotype :id_typeservice="service.type_service_chivic"></sp-portfoliotype>
    </div> -->
  </div>
</template>

<script>
//import axios from 'axios';
import { ref } from 'vue';
import server from './server';
import SpPortfoliotype from '../Portfolio/spPortfoliotype.vue';

export default {
  setup() {
    const services = ref([]);

    return {
      services,
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
  components: {
    SpPortfoliotype,
  },
  async created() {
    let response = await server.get('wp/v2/service_chivic?per_page=20&_embed');

    this.services = response.data;
    // response.data.forEach((element, i) => {
    //   setTimeout(() => {
    //     if (element.title.rendered != '') {
    //       this.services.push(element);
    //     }
    //   }, 1000 * i);
    // });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.mmm {
  position: relative;
}
.my-card {
  width: 100%;
}
.type_service_img {
  max-width: 200px;
}
.title_service {
  font-size: 36px;
  padding: 10px;
}
.content_service {
  font-size: 24px;
  padding: 10px;
}

.vry90-enter-active,
.vry90-leave-active {
  transition: all 1s ease 0.3s;
}

.vry90-enter-from,
.vry90-leave-to {
  opacity: 0;
}
</style>
