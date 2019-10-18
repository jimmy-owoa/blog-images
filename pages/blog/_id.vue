<template>
  <div class="container">
    <div class="card">
      <div class="card-body">
        <h1>{{articulo.title}}</h1>
        <p class="small">{{articulo.userName}}</p>
        <p>{{ articulo.body}}</p>
        <nuxt-link to="/blog" class="btn btn-primary">Atrás</nuxt-link>
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
        `https://jsonplaceholder.typicode.com/posts/${params.id}`
      );
      const articulo = res.data;
      
      const user = await axios.get(
        `https://jsonplaceholder.typicode.com/users/${res.data.userId}`
      );
      articulo.userName = user.data.name;
      return {articulo};
    } catch (error) {
      console.log(error)
      return { error: error}
    }
  }
};
</script>