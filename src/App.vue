<template>
  <div id="app">
    <img class="logo" alt="Vue logo" src="./assets/images/logo_vue.png">


    <h2 class="title"> {{ title }}</h2>

    <div class="filtre">
      <label for="filtre">Filtrer</label>
      <input type="text" id="filtre" v-model="inputFilter"/>

      <p class="nbFilm">Nombre de Films : {{ movies.length }}</p>
    </div>

    <div class="list">

      <Movie id="movies-list" v-for="movie in filteredArticles" v-bind:key="movie.id" :movie="movie"/>

      <div class="formulaire">
        <img class="form-img" src="./assets/images/logo-movie.png">
        <form>
          <div>

            <label for="title">Titre:</label>
            <input type="text" id="title" name="title" v-model="nouveau.title">
          </div>
          <div>
            <label for="insert-image">Image:</label>
            <input type="url" id="insert-image" name="insert-image" v-model="nouveau.image">
          </div>
          <div class="checkbox">
            <input type="checkbox" id="action" value="action" v-model="nouveau.genres">
            <label for="action">action</label>
            <input type="checkbox" id="Science-fiction" value="Science-fiction" v-model="nouveau.genres">
            <label for="Science-fiction">Science-fiction</label>
            <input type="checkbox" id="fantastique" value="fantastique" v-model="nouveau.genres">
            <label for="fantastique">fantastique</label>
            <input type="checkbox" id="horreur" value="horreur" v-model="nouveau.genres">
            <label for="horreur">horreur</label>
            <input type="checkbox" id="comedie" value="comedie" v-model="nouveau.genres">
            <label for="comedie">comedie</label>
          </div>
          <div>
            <label for="rating">Note:</label>
            <input type="number" id="rating" name="rating" min="0" max="10" v-model="nouveau.rating">
          </div>
          <div>
            <label for="review">Avis:</label>
            <input type="text" id="review" name="review" v-model="nouveau.review">
          </div>
          <div>
            <label for="description">Description:</label>
            <textarea type="text" id="description" name="description" v-model="nouveau.description"></textarea>
          </div>
          <div class="button">
            <button type="submit" v-on:click.prevent="addMovie">Ajouter nouveau film</button>
          </div>
        </form>
      </div>


    </div>
  </div>
</template>

<script>

import Movie from "./components/Movie";

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
          rating: 2000,
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
      nouveau: {
        id: null,
        title: null,
        image: null,
        genres: [],
        rating: null,
        review: null,
        description: null,
      }
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
    }
    ,
  }
  ,
  mounted() {
  }
}

</script>

<style lang="scss">

$primary-color-red:#DB0004;
$assomb-color:darken($primary-color-red,20%);

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 80px;
  padding-bottom: 20px;
  background: black;

}

.title {
  margin-top: 40px;
  padding-left: 40px;
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

form {
  border-top-style: solid;
  border-block-color: $primary-color-red;
}
</style>
