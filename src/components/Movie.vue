<template>

  <div class="list">


    <h3>{{ movie.id }}/ {{ movie.title.toUpperCase() }}</h3>
    <a :to="{name:'Movie', params:{id: movie.id}}"> <img class="imgMovie" :src="movie.image" width="300px"/> </a>
    <p> Genre:
    <ol class="genre" v-for="item in movie.genres" :key="item"> {{ item.toUpperCase() }}</ol>
    </p>
    <v-rating

        v-model="movie.rating"
        background-color="red lighten-3"
        color="yellow"
        length="10"
        large
    ></v-rating>
    <ol> Note :{{ movie.rating }}</ol>

  </div>


</template>

<script>
export default {
  name: "Movie",
  props: {
    id: {
      type: Number,
      default: 0
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
      type: String,
      default: "aucun"
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

.genre {
  display: inline-flex;
}

</style>