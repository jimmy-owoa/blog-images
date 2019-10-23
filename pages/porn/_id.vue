<template>
  <div class="container row">
    <div class="col-md-12">
      <h4>Página {{ this.$route.params.id }}</h4>
    </div>
    <div class="card" v-for="(item, index) in list.videos" :key="index">
      <div class="card-body">
        <a :href="item.video.embed_url" target="_blank" rel="noopener noreferrer">
          <b-img :src="item.video.thumb"></b-img>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData({isDev, route, store, env, params, query, req, res, redirect, error}){
    try {
      const res = await axios.get(
        `https://api.redtube.com/?data=redtube.Videos.searchVideos&output=json&category=Teen&page=${params.id}`
      );
      const list = res.data;
      return { list };
    } catch (error) {
      console.log(error);
      return { error: error };
    }
  }
};
</script>