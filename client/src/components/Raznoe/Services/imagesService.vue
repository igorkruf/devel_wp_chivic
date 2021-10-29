<template>
  <div class="col-12 col-md-10 mmm row justify-between">
    <!-- <div v-for="(url_image, i) in url_images" :key="i"> -->
    <q-img v-for="(url_image, i) in url_images" :key="i" :src="url_image" style="max-width: 150px; height: 150px" fit="contain" />
    <!-- </div> -->
  </div>
</template>

<script>
//import axios from 'axios';
//import { toRef } from 'vue';
import { ref } from 'vue';
import server from './server';

export default {
  props: {
    foto: {
      type: Array,
    },
  },
  setup(props) {
    let url_images = ref([]);
    console.log(props.foto[0]);
    let array_foto = props.foto[0].split(',');
    array_foto.forEach(async (element) => {
      let response = await server.get(`wp/v2/media/${element}`);
      url_images.value.push(response.data.source_url);
    });
    return {
      url_images,
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
  created() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.news_single {
  border: 0px solid red;
  text-align: justify;
}

.news_single:hover {
  cursor: pointer;
}
.miniatura_news {
  border: 0px solid red;
  width: 200px;
}
.title_news {
  text-align: left;
  border: 0px solid red;
  font-size: 18px;

  border-bottom: 1px solid #bdbdbd;
}
.mmm {
  position: relative;
  border: 1px solid red;
}
.mmm > div {
  border: 1px solid green;
}
</style>
