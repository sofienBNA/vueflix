<template>
  <v-app>
    <v-form
        ref="form"
        v-model="nouveau.valid"
        lazy-validation
    >
      <h2 class="form_title"> Ajout de Film</h2>
      <v-container>
        <v-row>
          <v-spacer/>
          <v-col cols="12" md="4">
            <v-text-field
                class="input"
                v-model="nouveau.title"
                :rules="nouveau.titleRules"
                label="TITRE"
                required
                placeholder="Champ obligatoire"
                dense
                rounded
                color="success"
            ></v-text-field>
          </v-col>
          <v-spacer/>
        </v-row>
        <v-row>
          <v-spacer/>
          <v-col cols="12" md="4">
            <v-text-field
                class="input"
                v-model="nouveau.image"
                :rules="nouveau.imageRules"
                label="URL IMAGE"
                placeholder="Rentrez un URL"
                dense
                rounded
                color="success"
                required
            ></v-text-field>
          </v-col>
          <v-spacer/>
        </v-row>
        <v-row>
          <v-spacer/>
          <v-rating class="rating "
                    v-model="nouveau.rating"
                    background-color="red "
                    color="yellow"
                    large
                    hover
                    length="10"
                    size="10"
                    required
          ></v-rating>
          <v-spacer/>
        </v-row>

        <!--checkbox-->

        <v-card-text>
          <v-container fluid>
            <v-row>
              <v-col
                  cols="12"
                  sm="4"
                  md="4"
              >
                <v-checkbox
                    v-model="nouveau.genres"
                    label="action"
                    color="red"
                    value="action"
                    dark
                ></v-checkbox>
                <v-checkbox
                    v-model="nouveau.genres"
                    label="Science-Fiction"
                    color="purple"
                    value="Science-Fiction"
                    dark
                ></v-checkbox>
              </v-col>
              <v-col
                  cols="12"
                  sm="4"
                  md="4"
              >
                <v-checkbox
                    v-model="nouveau.genres"
                    label="Fantastique"
                    color="indigo"
                    value="Fantastique"
                    dark
                ></v-checkbox>
                <v-checkbox
                    v-model="nouveau.genres"
                    label="Horreur"
                    color="orange"
                    value="Horreur"
                    dark
                ></v-checkbox>
              </v-col>
              <v-col
                  cols="12"
                  sm="4"
                  md="4"
              >
                <v-checkbox
                    v-model="nouveau.genres"
                    label="Comedie"
                    color="green"
                    value="Comedie"
                    dark
                ></v-checkbox>
                <v-checkbox
                    v-model="nouveau.genres"
                    label="Documentaire"
                    color="white"
                    value="Documentaire"
                    dark
                ></v-checkbox>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>


        <!--          boutton-->
        <v-row>
          <v-spacer/>
          <div class="text-center">
            <v-btn
                color="success"
                class="mr-4"
                @click="addMovieEvent"
            >
              Ajoutez Film
            </v-btn>
            <v-btn
                color="orange"
                class="mr-4"
                @click="resetEvent"
            >
              Reset Form
            </v-btn>
          </div>
          <v-spacer/>
        </v-row>
      </v-container>
    </v-form>
  </v-app>
</template>

<script>

export default {
  name: "MovieCreation",
  props: {
    movies: Array,
    addMovie: Function
  },
  data() {
    return {
      nouveau: {
        valid: true,
        id: null,
        title: null,
        titleRules: [v => !!v || 'Name is required'],
        image: null,
        imageRules: [v => !!v || 'URL is required'],
        genres: [],
        rating: null,
      },
    };
  },
  // addMovie() {
  //   this.movies.push({
  //         id: this.movies.length + 1,
  //         title: this.nouveau.title,
  //         image: this.nouveau.image,
  //         genres: this.nouveau.genres,
  //         rating: this.nouveau.rating,
  //         review: this.nouveau.review,
  //         description: this.nouveau.description
  //       }
  //   )
  //   console.log(this.nouveau)
  //   // .then(alert("Création réussie"));
  // },
  // reset() {
  //   this.$refs.form.reset()
  // },
  methods: {
    addMovieEvent() {
      this.$emit('addMovie-event', this.nouveau )
    },
    // resetEvent(){
    //   this.$emit('reset-event',this.plaload.$refs.form.reset())
    // }
  }
}

</script>

<style scoped>

</style>