<template>
  <div class="wrap_main row justify-center">
    <div class="col-12 col-md-10 q-ma-md wr column justify-between">
      <div class="slogan">
        <div class="ss">"Нужен сайт?"- Сделаю!</div>
      </div>
      <div class="wrk">
        <div class="kontact">звони: 8(902)264-69-69</div>
        <div class="kontact">пиши: igor-kruf@list.ru</div>
      </div>
    </div>
  </div>
</template>

<script>
//import axios from 'axios';
import { ref } from 'vue';
//import server from './server';
//import SpPortfoliotype from '../Portfolio/spPortfoliotype.vue';

export default {
  setup() {
    const nado_sdelayu = ref(['8(902)-264-69-69', 'igor-kruf@list.ru']);

    return {
      nado_sdelayu,
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
    //     let response = await server.get('wp/v2/service_chivic?per_page=20&_embed');
    //     this.services = response.data;
    //     // response.data.forEach((element, i) => {
    //     //   setTimeout(() => {
    //     //     if (element.title.rendered != '') {
    //     //       this.services.push(element);
    //     //     }
    //     //   }, 1000 * i);
    //     // });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.wrap_main {
  min-height: calc(100vh - 56px);
  background-image: url(../../assets/main_big4.png);
  background-attachment: scroll;
  background-repeat: no-repeat;
  background-position: right bottom;
  background-size: auto 75%;
  border: 0px solid red;
  font-family: Arial, Helvetica, sans-serif;
}
@media (max-width: 700px) {
  .wrap_main {
    background: none;
  }
}
.slogan {
  border: 0px solid red;
  margin: 10%;
}
.wrk {
  border: 0px solid red;
  margin: 10%;
}
.kontact {
  border: 0px solid green;
  font-size: 18px;
}
.ss {
  font-size: 36px;
}
.main_info {
  border: 1px solid red;
  height: 100%;
}

.main_img {
  border: 1px solid green;
  height: 100%;
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
