<template>

  <v-app>
    <div class="list">
      <h3>{{ movie.id }}/ {{ movie.title.toUpperCase() }}</h3>
      <a :to="{name:'Movie', params:{id: movie.id}}">
        <router-link :to="{name:'Movie', params:{id:movie.id, movie:movie}}">
          <img class="imgMovie" :src="movie.image" width="300px"/>
        </router-link>
      </a>
      <p> Genre:</p>
      <ol class="genre" v-for="item in movie.genres" :key="item"> {{ item.toUpperCase() }}</ol>
      <v-rating
          class="rate"
          :value="movie.rating"
          background-color="red lighten-3"
          color="yellow"
          length="10"
          large
          readonly
      ></v-rating>
    </div>
  </v-app>


</template>

<script>
export default {
  name: "Movie",
  props: {
    id: {
      type: Number,
      default: null
    },
    title: {
      type: String,
      default: "aucun"
    },
    image: {
      type: String,
      default: "https://img.daf-mag.fr/Img/BREVE/2018/10/334316/Tribune-URSSAF-droit-erreur-vos-nouveaux-rapports-administration-F.jpg",
    },
    genres: {
      type: Array,
    },
    rating: {
      type: Number,
      default: 0,
    },
    review: {
      type: String,
      default: "aucun avis",
    },
    description: {
      type: String,
      default: "aucune description"
    },
    movie: Object,
  },
  data() {
    return {}
  },

}
</script>

<style scoped>
.imgMovie {
  border: groove
}

.list{
  color: white
;
}
.genre{
  display:inline-flex;
}


</style>