<template>
  <div>
    <SectionTitle :sectionSubtitle="subtitle" />
    <!-- SNACKBAR -->
    <v-snackbar
      v-model="snackbar"
      height="50px"
      color="info"
      tile
    >
      Added to <span class="secondary darken-1 pa-2 rounded ml-2"> {{ category }} </span>
    </v-snackbar>

    <!-- BUTTON FOR MENU EXPAND IN MOBILE DEVICES -->
    <div class="text-center" id="years-menu-btn">
      <v-btn icon @click="expand = !expand">
        <v-icon color="cyan">mdi-menu</v-icon>
      </v-btn>
    </div>

    <!-- MENU EXPAND IN MOBILE DEVICES  -->
    <v-expand-transition>
      <v-row id="years-menu" v-show="expand">
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2010')"
        >
          2010
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2011')"
        >
          2011
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2012')"
        >
          2012
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2013')"
        >
          2013
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2014')"
        >
          2014
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2015')"
        >
          2015
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2016')"
        >
          2016
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2017')"
        >
          2017
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2018')"
        >
          2018
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2019')"
        >
          2019
        </v-col>
        <v-col
          class="year-col"
          v-on:click="
            expand = !expand;
          "
          @click="getMoviesByYear('2020')"
        >
          2020
        </v-col>
      </v-row>
    </v-expand-transition>

    <v-tabs class="bar-tabs" centered background-color="transparent">
      <v-tabs-slider color="cyan"></v-tabs-slider>
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2010')"
        >2010</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('211')"
        >2011</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2012')"
        >2013</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2013')"
        >2012</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2014')"
        >2014</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2015')"
        >2015</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2016')"
        >2016</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2017')"
        >2017</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2018')"
        >2018</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2019')"
        >2019</v-tab
      >
      <v-tab
        active-class="cyan--text"
        class="white--text tab"
        @click="getMoviesByYear('2020')"
        >2020</v-tab
      >
    </v-tabs>

    <div id="year-selected-mobile">{{ year }}</div>

    <div class="moviesColumns" v-show="panelExpanded">
      <v-row no-gutters>
        <v-col md="3" xs="12" v-for="(item, i) in moviesByYear" :key="'B' + i">
          <div class="fadeIn">
            <v-card class="transparent mb-15" outlined>
              <v-row no-gutters class="d-flex justify-start">
                <v-col md="8" xs="12">
                  <!-- MOVIE IMAGE AND DYNAMIC ICONS -->
                  <v-img :src="url + item.poster_path" class="movie-img">
                    <v-icon
                      class="eye-icon-img"
                      v-show="watchedMovies.includes(item) ? watched : !watched"
                      v-model="watched"
                      >mdi-eye</v-icon
                    >
                    <v-icon
                      class="heart-icon-img"
                      v-show="favoriteMovies.includes(item) ? favorite : !favorite"
                      >mdi-heart</v-icon
                    >
                    <v-icon
                      class="plus-icon-img"
                      v-show="toWatchMovies.includes(item) ? towatch : !towatch"
                      >mdi-plus</v-icon
                    >

                    <div>
                      <div class="rate-img">
                        {{ item.rate }}
                      </div>
                    </div>
                  </v-img>
                  <!-- **************************************** -->
                  <h3 class="movie-title ma-auto">{{ item.title }}</h3>
                </v-col>
                <v-col md="4" xs="12">
                  <div class="mt-10" id="btn-column">
                    <!-- BUTTON - WATCHED MOVIE  -->
                    <v-tooltip bottom>
                      <template v-slot:activator="{ on, attrs }">
                        <v-btn
                          small
                          color="blue"
                          class="white--text d-block mt-5 mx-2"
                          v-bind="attrs"
                          v-on="on"
                          @click="addWatched(item)"
                          :disabled="watchedMovies.includes(item) ? watched : !watched"
                          ><v-icon>mdi-eye</v-icon></v-btn
                        >
                      </template>
                      <span>Add to watched movies</span>
                    </v-tooltip>
                    <!-- BUTTON - FAVORITE MOVIE  -->
                    <v-btn
                      small
                      color="red"
                      class="white--text d-block mt-5 mx-2"
                      @click="addFavorite(item)"
                      :disabled="favoriteMovies.includes(item) ? favorite : !favorite"
                      ><v-icon>mdi-heart</v-icon></v-btn
                    >

                    <v-dialog transition="dialog-bottom-transition" max-width="600">
                      <template v-slot:activator="{ on, attrs }">
                        <div color="primary" v-bind="attrs" v-on="on">
                          <!-- BUTTON - TO RATE MOVIE  -->
                          <v-tooltip bottom>
                            <template v-slot:activator="{ on2, attrs2 }">
                              <v-btn
                                small
                                color="purple"
                                class="white--text d-block mt-5 mx-2"
                                v-bind="attrs2"
                                v-on="on2"
                                ><v-icon>mdi-numeric</v-icon></v-btn
                              >
                            </template>
                            <span>Rate movie</span>
                          </v-tooltip>
                        </div>
                      </template>
                      <template v-slot:default="rateDialog">
                        <v-card>
                          <v-toolbar color="primary" dark
                            >{{ item.title }}

                            <v-btn
                              icon
                              depressed
                              class="ml-auto"
                              @click="rateDialog.value = false"
                              ><v-icon>mdi-close</v-icon></v-btn
                            >
                          </v-toolbar>

                          <v-card-text>
                            <div class="pa-12">
                              <h4 class="text-center">Rate the movie</h4>
                              <div class="text-center primary--text m-5" id="rate-number">
                                {{ value / 10 }}
                              </div>
                              <!-- RATE THE MOVIE -->
                              <form>
                                <v-slider
                                  v-model="value"
                                  step="5"
                                  class="mt-10"
                                ></v-slider>
                                <v-btn
                                  block
                                  color="secondary"
                                  @click="addRate(item)"
                                  v-on:click="rateDialog.value = false"
                                  >Done</v-btn
                                >
                              </form>
                            </div>
                          </v-card-text>
                        </v-card>
                      </template>
                    </v-dialog>

                    <!-- BUTTON - TO WATCH MOVIE  -->
                    <v-tooltip bottom>
                      <template v-slot:activator="{ on, attrs }">
                        <v-btn
                          small
                          color="indigo darken-2"
                          class="white--text d-block mt-5 mx-2"
                          v-bind="attrs"
                          v-on="on"
                          @click="addToWatch(item)"
                          ><v-icon>mdi-plus</v-icon></v-btn
                        >
                      </template>
                      <span>Add to to-watch list</span>
                    </v-tooltip>
                  </div>
                </v-col>
              </v-row>
            </v-card>
          </div>
        </v-col>
      </v-row>
    </div>
  </div>
</template>

<script>
import SectionTitle from "../components/SectionTitle";
import { mapState, mapActions } from "vuex";
import axios from "axios";

export default {
  name: "Ranking",
  components: {
    SectionTitle,
  },
  data() {
    return {
      subtitle: "Popular films of the last decade",
      url: "https://image.tmdb.org/t/p/original",
      userID: null,
      year: '',
      snackbar: false,
      category: '',
      rateDialog: false,
      expand: false,
      errorMessage: "",
      panelExpanded: false,
      arrWatched: [],
      arrToWatch: [],
      arrRated: [],
      arrFavorite: [],
      rated: true,
      favorite: true,
      watched: true,
      towatch: true,
      rated: true,
      value: 0,
      moviesByYear: [],
      userData: []
    };
  },
  computed: {
    ...mapState(["toWatchMovies", "watchedMovies", "favoriteMovies", "moviesWithRates"]),
  },
  created() {
    this.getMoviesByYear('2010')
    this.getUserID()
  },
  methods: {
    showSnackbar (category) {
    this.snackbar = true
    this.category = category
    },
    getMoviesByYear(year) {
      this.year = year
      const url = "https://api.themoviedb.org/3";
      const apikey = "c9a3e87b703c630c13d5ea61ef62c7b6";
      const moviesUrl = `${url}/discover/movie?year=${year}&api_key=${apikey}&sort_by=popularity.desc&page=1`;

      return new Promise(() => {
        axios
          .get(moviesUrl)
          .then((resp) => {
            this.panelExpanded = true;
            this.moviesByYear = resp.data.results;
          })
          .catch((e) => {
            console.info(e);
            this.errorMessage =
              "The answer is taking too long. There may have been an error with the database. Please reload the website.";
          });
      });
    },
    getUserID () {
      const userID= JSON.parse(localStorage.getItem("USERID")) || {};
      this.userID = userID.id
    },
    // **** LOCALSTORAGE FUNCTIONS **** //
    addWatched(item) {
      this.showSnackbar('Watched Movies')
      this.watchedMovies.push(item);

      const json = { rate: this.value / 10, movie: item };

      this.writeMovieData(json, 'isWatched')

      const storage = JSON.parse(localStorage.getItem("storageWatchedMovies")) || [];
      storage.push(json);
      localStorage.setItem("storageWatchedMovies", JSON.stringify(storage));
    },
    addFavorite(item) {
      this.showSnackbar('Favorite Movies')
      this.favoriteMovies.push(item);

      const json = { rate: this.value / 10, movie: item };

      this.writeMovieData(json, 'isFavorite')
a
    },
    addRate(item) {
      this.showSnackbar('Rated Movies')

      const value = this.value / 10;
      const json = {};

      this.ratedMovies = item;
      this.ratedMovies.rate = value;

      json.movie_data = this.ratedMovies;
      json.rate = this.ratedMovies.rate;

      this.writeMovieData(json, 'isRated')

      const storage = JSON.parse(localStorage.getItem("storageRatedMovies")) || [];
      storage.push(json);
      localStorage.setItem("storageRatedMovies", JSON.stringify(storage));

      // ************************ //
      this.moviesByYear.rate = value;
    },
    addToWatch(item) {
      this.showSnackbar('To Watch Movies')
      this.toWatchMovies.push(item);

      const json = { rate: this.value / 10, movie: item };

      this.writeMovieData(json, 'isToWatch')

      const storage = JSON.parse(localStorage.getItem("storageToWatchMovies")) || [];
      storage.push(json);
      localStorage.setItem("storageToWatchMovies", JSON.stringify(storage));
    },
    writeMovieData(json, type) {
      const storage = JSON.parse(localStorage.getItem("storageUserDATA")) || [];
      if(type === 'isWatched') {
        storage[this.userID].watchedMovies.push(json)
      }
      if(type === 'isFavorite') {
        storage[this.userID].favoriteMovies.push(json)
      }
      if(type === 'isRated') {
        storage[this.userID].ratedMovies.push(json)
      }
      if(type === 'isToWatch') {
        storage[this.userID].toWatchMovies.push(json)
      }
      localStorage.setItem("storageUserDATA", JSON.stringify(storage));
    }
  }
};
</script>

<style lang="scss" scoped>
@import "src/scss/variables";

.fadeIn {
  animation: fadeIn 1s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.eye-icon-img {
  color: white !important;
  text-shadow: none !important;
  background: #2196f3;
  padding: 10px;
  border-radius: 0px 10px 0px 0px;
  position: absolute;
  bottom: 0px;
  left: 0px;
}
.heart-icon-img {
  color: $secondary !important;
  text-shadow: none !important;
  background: white;
  padding: 10px;
  border-radius: 10px 0px 0px 0px;
  position: absolute;
  bottom: 0px;
  right: 0px;
}

.plus-icon-img {
  position: absolute;
  top: 0px;
  left: 0px;
  padding: 10px;
  border-radius: 0px 0px 10px 0px;
  background: #404ea7;
  color: white;
  text-shadow: none;
}
.rate-img {
  color: white !important;
  text-shadow: none !important;
  background: #a438b6;
  font-size: 20px;
  font-family: $style2;
  letter-spacing: 0px;
  width: 50%;
  border-radius: 0px 0px 0px 10px;
  text-align: center;
  position: absolute;
  top: 0px;
  right: 0px;
}

.rate-input {
  font-size: 1em;
  height: 100%;
  width: 100%;
  padding: 100px;
  border: 2px solid $primary;
  border-radius: 10px;

  &:focus {
    outline: none;
  }
}

// ******* MOBILE RESPONSIVE ******* //
@media only screen and (min-width: 360px) {
  .section-subtitle {
    font-family: $style3;
    font-size: 1em;
    text-align: center;
    margin-bottom: 20px;
    letter-spacing: 4px;
    background: url("../assets/img/background5.jpg");
    background-repeat: repeat;
    color: rgb(255, 212, 212) !important;
    text-shadow: 0px 0px 10px $secondary;
    animation: move 2s ease-in-out;
  }

  #rate-number {
    font-size: 3em;
  }

  @keyframes move {
    from {
      margin-left: -3000px;
      opacity: 0;
    }
    to {
      margin-left: 0px;
      opacity: 1;
    }
  }

  #year-selected-mobile {
    display: block;
    text-align: center;
    font-size: 2em;
    margin-bottom: 50px;
    margin-top: 50px;
    color: cyan;
  }

  .year {
    text-align: center;
  }

  .header {
    align-self: center !important;
    font-family: $style3;
    font-weight: lighter;
    font-size: 6em !important;
    background-color: $dark2 !important;
    color: $secondary;

    &:hover {
      color: white;
      transition: color 1s;
    }

    &:focus {
      outline: none;
    }
  }

  #btn-column {
    display: flex !important;
    padding-left: 30px;
    padding-right: 30px;
    justify-content: center;
  }

  .moviesColumns {
    text-align: center;
    background: $dark2;
    color: white;
    text-shadow: 0px 0px 3px $secondary, 0px 0px 5px red;
    margin-bottom: 100px;
  }

  .movie-img {
    width: 300px;
    border-radius: 10px 10px 10px 10px !important;
    padding: 15px;
    height: auto;
    margin: 0 auto;
  }

  .movie-title {
    font-weight: lighter;
    font-size: 24px;
    padding-top: 20px;
    color: white;
  }

  .bar-tabs {
    display: none;
  }

  #years-menu-btn {
    display: block;
  }

  #years-menu {
    margin: 10px;
    text-align: center;
  }

  .year-col {
    margin: 5px;
    border-radius: 20px;
    color: $dark2;
    font-weight: bold;
    background: $primary;
    font-family: $style3;

    &:hover {
      cursor: pointer;
    }
  }
}
// ******* LAPTOP RESPONSIVE ******* //
@media only screen and (min-width: 767px) {
  .section-subtitle {
    font-family: $style3;
    font-size: 2em;
    text-align: center;
    margin-bottom: 20px;
    letter-spacing: 4px;
    background: url("../assets/img/background5.jpg");
    background-repeat: repeat;
    color: rgb(255, 212, 212) !important;
    text-shadow: 0px 0px 10px $secondary;
    animation: move 2s ease-in-out;
  }

  @keyframes move {
    from {
      margin-left: -3000px;
      opacity: 0;
    }
    to {
      margin-left: 0px;
      opacity: 1;
    }
  }

  .year {
    text-align: center;
  }

  #rate-number {
    font-size: 5em;
  }

  .header {
    align-self: center !important;
    font-family: $style3;
    font-weight: lighter;
    font-size: 8em !important;
    background-color: $dark2 !important;
    color: $secondary;

    &:hover {
      color: white;
      transition: color 1s;
    }

    &:focus {
      outline: none;
    }
  }

  #year-selected-mobile {
    display: none;
  }

  #btn-column {
    display: block !important;
    padding-left: 0px;
    padding-right: 0px;
    justify-content: center;
  }

  .moviesColumns {
    text-align: center;
    background: $dark2;
    letter-spacing: 5px;
    color: white;
    text-shadow: 0px 0px 3px $secondary, 0px 0px 5px red;
    margin-bottom: 100px;
  }

  .movie-img {
    width: 220px;
    margin: 20px;
    padding: 0px;
    height: auto;
    border-radius: 10px 10px 10px 10px !important;
    box-shadow: 0px 5px 10px black;
  }

  .movie-title {
    font-weight: lighter;
    font-size: 1em;
    color: white;
  }

  .bar-tabs {
    display: block;
  }

  #years-menu-btn {
    display: none;
  }
}

// ******* DESKTOP RESPONSIVE ******* //
@media only screen and (min-width: 1370px) {
  .section-subtitle {
    font-family: $style3;
    font-size: 2em;
    text-align: center;
    margin-bottom: 20px;
    letter-spacing: 4px;
    background: url("../assets/img/background5.jpg");
    background-repeat: repeat;
    color: rgb(255, 212, 212) !important;
    text-shadow: 0px 0px 10px $secondary;
    animation: move 2s ease-in-out;
  }

  @keyframes move {
    from {
      margin-left: -3000px;
      opacity: 0;
    }
    to {
      margin-left: 0px;
      opacity: 1;
    }
  }

  .year {
    text-align: center;
  }

  .header {
    align-self: center !important;
    font-family: $style3;
    font-weight: lighter;
    font-size: 8em !important;
    background-color: $dark2 !important;
    color: $secondary;

    &:hover {
      color: white;
      transition: color 1s;
    }

    &:focus {
      outline: none;
    }
  }

  #year-selected-mobile {
    display: none;
  }

  #btn-column {
    margin-right: 0 auto;
    justify-content: left;
  }

  #rate-number {
    font-size: 6em;
  }

  .moviesColumns {
    text-align: center;
    background: $dark2;
    color: white;
    text-shadow: 0px 0px 3px $secondary, 0px 0px 5px red;
    margin-bottom: 100px;
  }

  .movie-img {
    width: 300px;
    margin: 20px;
    padding: 0px;
    height: auto;
    border-radius: 10px 10px 10px 10px !important;
    box-shadow: 0px 5px 10px black;
  }

  .movie-title {
    font-weight: lighter;
    font-size: 1.5em;
    color: white;
  }

  .bar-tabs {
    display: block;
  }

  #years-menu-btn {
    display: none;
  }
}
</style>
