<template>
  <div id="app">
    <v-app>
      <img class="logo" alt="Vue logo" src="../assets/images/logo_vue.png">

      <h2 class="title"> {{ title }}</h2>

      <!--      bar de filtrage-->
      <div class="filtre">
        <v-container>
          <v-row>
            <v-col
                cols="12"
                sm="6"
            >
              <v-text-field
                  label="Filtrer"
                  outlined
                  type="text"
                  id="filtre"
                  v-model="inputFilter"
                  dark
                  color="success"
              ></v-text-field>
            </v-col>
          </v-row>
        </v-container>
        <p class="nbFilm">Nombre de Films : {{ filteredArticles.length }}</p>
      </div>

      <router-link :to="{name:'moviecreation'}">
        <v-btn> Formulaire d'ajout </v-btn>
      </router-link>
      <!--      list film-->
      <div class="list">

        <Movie v-for="movie in filteredArticles" v-bind:key="movie.id" :movie="movie" />

      </div>

    </v-app>
  </div>
</template>

<script>

import Movie from "../components/Movie";

export default {
  name: "App",
  components: {
    Movie,
  },
  data: function () {
    return {
      title: "Bienvenue sur VueFlix !",
      // On peut rajouter nos films ici
      movies: [{
        id: 1,
        title: "Parasite",
        image: "https://fr.web.img6.acsta.net/pictures/20/02/12/13/58/3992754.jpg",
        genres: ["comedy", "drama", "thriller"],
        rating: 9,
        review: "With an insightful and searing exploration of human behavior, ‘Parasite’ is a masterfully crafted film that is a definite must watch.",
        description: "Parasite (Korean: 기생충; RR: Gisaengchoong) is a 2019 South Korean black comedy thriller film directed by Bong Joon-ho, who also co-wrote the screenplay with Han Jin-won.",
      },
        {
          id: 2,
          title: "Lord of the Rings",
          image: "https://m.media-amazon.com/images/M/MV5BN2EyZjM3NzUtNWUzMi00MTgxLWI0NTctMzY4M2VlOTdjZWRiXkEyXkFqcGdeQXVyNDUzOTQ5MjY@._V1_.jpg",
          genres: ["action", "fantastique", "aventure"],
          rating: 10,
          review: "With an insightful and searing exploration of human behavior, ‘Parasite’ is a masterfully crafted film that is a definite must watch.",
          description: "bilbon mes couilles",
        },
        {
          id: 3,
          title: "Star Wars III",
          image: "https://fr.web.img3.acsta.net/medias/nmedia/18/35/53/23/18423997.jpg",
          genres: ["action", "SF", "complotisme"],
          rating: 10,
          review: "With an insightful and searing exploration of human behavior, ‘Parasite’ is a masterfully crafted film that is a definite must watch.",
          description: "i have a bad felling about this",
        },
      ],
      inputFilter: "",
      // nouveau: {
      //   valid: true,
      //   id: null,
      //   title: null,
      //   titleRules: [v => !!v || 'Name is required'],
      //   image: null,
      //   imageRules: [v => !!v || 'URL is required'],
      //   genres: [],
      //   rating: null,
      //   review: null,
      //   description: null,
      // }
    };
  },
  computed: {
    filteredArticles() {
      if (this.inputFilter === "") {
        return this.movies
      } else {
        // return this.movies.filter(element => element.genres.includes( this.inputFilter))ZS
        return this.movies.filter((element) => {
          return element.title.toLowerCase().match(this.inputFilter);
        })
      }
    },
  },
  methods: {
    addMovie(nouveau) {
      this.movies.push({
            id: this.movies.length + 1,
            title: nouveau.title,
            image: nouveau.image,
            genres: nouveau.genres,
            rating: nouveau.rating,
            review: nouveau.review,
            description: nouveau.description
          }
      )
      console.log(this)
      // .then(alert("Création réussie"));
    },
    // reset(playload) {
    //   this.playload
    // },
  },

}
</script>


<style lang="scss">
$primary-color-red: #DB0004;
$assomb-color: darken($primary-color-red, 20%);
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  //padding-top: 80px;
  //padding-bottom: 20px;
  background: black;
}

.title {
  font-size: x-large;
  padding-left: 20px;
  text-decoration: underline;
  text-decoration-color: $primary-color-red;
  color: white;
}

.filtre {
  display: inline-grid;
  color: white;
}

.list {
  border-top-style: solid;
  border-block-color: $primary-color-red;
  color: white;
}

#movies-list {
  text-align: center;
  color: white;
}

.logo {
  border: ridge;
}

.form-img {
  margin-top: 20px;
}

.formulaire {
  color: white;
  border-top-style: solid;
  border-block-color: $primary-color-red;
  text-align: end;
  display: inline-table;
}

.form_title {
  text-align: center;
  border-top-style: solid;
  border-block-color: $primary-color-red;
  color: white;
}

.input {
  background-color: white;
  color: chartreuse;
}

.form_title {
  text-decoration: underline;
  text-decoration-color: $primary-color-red;
}
</style>