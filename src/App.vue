<template>
  <div id="app">
    <v-app>
      <img class="logo" alt="Vue logo" src="./assets/images/logo_vue.png">


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

<!--      list film-->
      <div class="list">

        <Movie id="movies-list" v-for="movie in filteredArticles" v-bind:key="movie.id" :movie="movie"/>
      </div>

<!--      formulaire d'ajout-->
<!--      <v-form-->
<!--          ref="form"-->
<!--          v-model="nouveau.valid"-->
<!--          lazy-validation-->
<!--      >-->
<!--        <h2 class="form_title"> Ajout de Film</h2>-->
<!--        <v-container>-->
<!--          <v-row>-->
<!--            <v-spacer/>-->
<!--            <v-col cols="12" md="4">-->
<!--              <v-text-field-->
<!--                  class="input"-->
<!--                  v-model="nouveau.title"-->
<!--                  :rules="nouveau.titleRules"-->
<!--                  label="TITRE"-->
<!--                  required-->
<!--                  placeholder="Champ obligatoire"-->
<!--                  dense-->
<!--                  rounded-->
<!--                  color="success"-->
<!--              ></v-text-field>-->
<!--            </v-col>-->
<!--            <v-spacer/>-->
<!--          </v-row>-->
<!--          <v-row>-->
<!--            <v-spacer/>-->
<!--            <v-col cols="12" md="4">-->
<!--              <v-text-field-->
<!--                  class="input"-->
<!--                  v-model="nouveau.image"-->
<!--                  :rules="nouveau.imageRules"-->
<!--                  label="URL IMAGE"-->
<!--                  placeholder="Rentrez un URL"-->
<!--                  dense-->
<!--                  rounded-->
<!--                  color="success"-->
<!--                  required-->
<!--              ></v-text-field>-->
<!--            </v-col>-->
<!--            <v-spacer/>-->
<!--          </v-row>-->
<!--          <v-row>-->
<!--            <v-spacer/>-->
<!--            <v-rating class="rating "-->
<!--                      v-model="nouveau.rating"-->
<!--                      background-color="red "-->
<!--                      color="yellow"-->
<!--                      large-->
<!--                      hover-->
<!--                      length="10"-->
<!--                      size="10"-->
<!--                      required-->
<!--            ></v-rating>-->
<!--            <v-spacer/>-->
<!--          </v-row>-->

<!--          &lt;!&ndash;checkbox&ndash;&gt;-->

<!--          <v-card-text>-->
<!--            <v-container fluid>-->
<!--              <v-row>-->
<!--                <v-col-->
<!--                    cols="12"-->
<!--                    sm="4"-->
<!--                    md="4"-->
<!--                >-->
<!--                  <v-checkbox-->
<!--                      v-model="nouveau.genres"-->
<!--                      label="action"-->
<!--                      color="red"-->
<!--                      value="action"-->
<!--                      dark-->
<!--                  ></v-checkbox>-->
<!--                  <v-checkbox-->
<!--                      v-model="nouveau.genres"-->
<!--                      label="Science-Fiction"-->
<!--                      color="purple"-->
<!--                      value="Science-Fiction"-->
<!--                      dark-->
<!--                  ></v-checkbox>-->
<!--                </v-col>-->
<!--                <v-col-->
<!--                    cols="12"-->
<!--                    sm="4"-->
<!--                    md="4"-->
<!--                >-->
<!--                  <v-checkbox-->
<!--                      v-model="nouveau.genres"-->
<!--                      label="Fantastique"-->
<!--                      color="indigo"-->
<!--                      value="Fantastique"-->
<!--                      dark-->
<!--                  ></v-checkbox>-->
<!--                  <v-checkbox-->
<!--                      v-model="nouveau.genres"-->
<!--                      label="Horreur"-->
<!--                      color="orange"-->
<!--                      value="Horreur"-->
<!--                      dark-->
<!--                  ></v-checkbox>-->
<!--                </v-col>-->
<!--                <v-col-->
<!--                    cols="12"-->
<!--                    sm="4"-->
<!--                    md="4"-->
<!--                >-->
<!--                  <v-checkbox-->
<!--                      v-model="nouveau.genres"-->
<!--                      label="Comedie"-->
<!--                      color="green"-->
<!--                      value="Comedie"-->
<!--                      dark-->
<!--                  ></v-checkbox>-->
<!--                  <v-checkbox-->
<!--                      v-model="nouveau.genres"-->
<!--                      label="Documentaire"-->
<!--                      color="white"-->
<!--                      value="Documentaire"-->
<!--                      dark-->
<!--                  ></v-checkbox>-->
<!--                </v-col>-->
<!--              </v-row>-->
<!--            </v-container>-->
<!--          </v-card-text>-->


<!--          &lt;!&ndash;          boutton&ndash;&gt;-->
<!--          <v-row>-->
<!--            <v-spacer/>-->
<!--            <div class="text-center">-->
<!--              <v-btn-->
<!--                  color="success"-->
<!--                  class="mr-4"-->
<!--                  @click="addMovie"-->
<!--              >-->
<!--                Ajoutez Film-->
<!--              </v-btn>-->
<!--              <v-btn-->
<!--                  color="orange"-->
<!--                  class="mr-4"-->
<!--                  @click="reset"-->
<!--              >-->
<!--                Reset Form-->
<!--              </v-btn>-->
<!--            </div>-->
<!--            <v-spacer/>-->
<!--          </v-row>-->
<!--        </v-container>-->
<!--      </v-form>-->
      <MovieCreation/>
    </v-app>
  </div>
</template>

<script>

import Movie from "./components/Movie";
import MovieCreation from "./components/MovieCreation";
export default {
  name: "App",
  components: {
    Movie,
    MovieCreation
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
    addMovie() {
      this.movies.push({
            id: this.movies.length + 1,
            title: this.nouveau.title.toUpperCase(),
            image: this.nouveau.image,
            genres: this.nouveau.genres,
            rating: this.nouveau.rating,
            review: this.nouveau.review,
            description: this.nouveau.description
          }
      )
      console.log(this.nouveau)
      // .then(alert("Création réussie"));
    },
    reset() {
      this.$refs.form.reset()
    },
  },
  mounted() {
  }
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

.form_title{
  text-decoration: underline;
  text-decoration-color: $primary-color-red;
}
</style>
