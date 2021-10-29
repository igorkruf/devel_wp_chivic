<template>
  <div>
    <!-- ////////////////////////////////////// -->
    <div v-if="portfolio.length == 0">fsdfsdfsd</div>
    <div v-else class="row col-12 col-md-10 mmm">
      <transition-group name="pts" appear>
        <q-card v-for="(pf, i) in portfolio" :key="i" class="column justify-between col-10 col-sm-3 col-xl-2 col-xxl-1 q-ma-md my-card" square flat fit="contain">
          <q-img :src="pf.miniature" class="pit_img" no-spinner />

          <q-card-section class="cpt">
            <a :href="pf.url[0]" class="text-subtitle1 text-justify">{{ pf.url[0] }}</a>
            <div v-html="pf.content2" class="text-caption text-justify"></div>
          </q-card-section>
        </q-card>
      </transition-group>
    </div>
    <!-- ////////////////////////////////////////// -->
    <!-- <q-card v-for="(pf, i) in portfolio" :key="i" class="col-2">
      <q- class="col-2">
        
        <q-img :src="pf.miniature" fit="contain" />
      {{ pf.url }}
        
        </q-card> 
      <q-img :src="pf.miniature" fit="contain" />
      {{ pf.url }}
    </div> -->
  </div>
</template>

<script>
//import axios from 'axios';
import { ref } from 'vue';
import server from './server';

export default {
  props: {
    id_typeservice: Array,
  },
  setup() {
    const portfolio = ref([]);

    return {
      portfolio,
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
    let response = await server.get(`myplugin/v15/portfolio-type/${this.id_typeservice}`);
    console.log(response.data);
    response.data.forEach((element, i) => {
      setTimeout(() => {
        if (element.title.rendered != '') {
          this.portfolio.push(element);
        }
      }, 500 * i);
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.my-card {
  height: 300px;
}
.pit_img {
  max-height: 200px;
}
.pts-enter-active,
.pts-leave-active {
  transition: all 1s ease;
}

.pts-enter-from,
.pts-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>
