<template>
  <div class="container">
    <div class="card">
      <div class="card-body">
        <h4>Author: {{image.user.name}}</h4>
        <h4>Portfolio: <a :href="image.user.portfolio_url" target="_blank" rel="noopener noreferrer">{{image.user.portfolio_url}}</a></h4>
        <b-img :src="image.urls.regular" fluid alt="Responsive image"></b-img>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { async } from 'q';
export default {
  async asyncData({isDev, route, store, env, params, query, req, res, redirect, error}){
    try {
      const res = await axios.get(
        `https://api.unsplash.com/photos/random/?client_id=0d82ef17500ac5ef1528516541237c6a8341c97a681b028071e07bcf4dd7e61b`
      );
      const image = res.data;
      return {image};
    }catch(error){
      return {error: error};
    }
  }
}
</script>