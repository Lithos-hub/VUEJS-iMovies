<template>
  <div>
    <SectionTitle :sectionName="name" />

    <div>
      <v-dialog
        class="dialog"
        v-model="dialog1"
        v-if="dialog1"
        fullscreen
        overlay-opacity="10"
      >
        <v-card height="100%" class="cardDialog">
          <div class="row videoDialog">
            <v-sheet
              color="error"
              width="100%"
              height="100%"
              dark
              class="pa-5"
              v-if="movieError1.length != 0"
            >
              <h1 class="video-error">{{ movieError1 }}</h1>
            </v-sheet>

            <iframe
              width="350"
              height="900"
              class="video"
              :src="trailer1"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
          </div>

          <div class="closeDialog-btn">
            <v-btn color="error" block @click="dialog1 = false"> Close </v-btn>
          </div>
        </v-card>
      </v-dialog>
      <v-dialog
        class="dialog"
        v-model="dialog2"
        v-if="dialog2"
        fullscreen
        overlay-opacity="10"
      >
        <v-card height="100%" class="cardDialog">
          <div class="row videoDialog">
            <v-sheet
              color="error"
              width="100%"
              height="100%"
              dark
              class="pa-5"
              v-if="movieError2.length != 0"
            >
              <h1 class="video-error">{{ movieError2 }}</h1>
            </v-sheet>

            <iframe
              width="350"
              height="900"
              class="video"
              :src="trailer2"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
          </div>

          <div class="closeDialog-btn">
            <v-btn color="error" block @click="dialog2 = false"> Close </v-btn>
          </div>
        </v-card>
      </v-dialog>
      <v-dialog
        class="dialog"
        v-model="dialog3"
        v-if="dialog3"
        fullscreen
        overlay-opacity="10"
      >
        <v-card height="100%" class="cardDialog">
          <div class="row videoDialog">
            <v-sheet
              color="error"
              width="100%"
              height="100%"
              dark
              class="pa-5"
              v-if="movieError3.length != 0"
            >
              <h1 class="video-error">{{ movieError3 }}</h1>
            </v-sheet>

            <iframe
              width="350"
              height="900"
              class="video"
              :src="trailer3"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
          </div>

          <div class="closeDialog-btn">
            <v-btn color="error" block @click="dialog3 = false"> Close </v-btn>
          </div>
        </v-card>
      </v-dialog>
      <v-dialog
        class="dialog"
        v-model="dialog4"
        v-if="dialog4"
        fullscreen
        overlay-opacity="10"
      >
        <v-card height="100%" class="cardDialog">
          <div class="row videoDialog">
            <v-sheet
              color="error"
              width="100%"
              height="100%"
              dark
              class="pa-5"
              v-if="movieError4.length != 0"
            >
              <h1 class="video-error">{{ movieError4 }}</h1>
            </v-sheet>

            <iframe
              width="350"
              height="900"
              class="video"
              :src="trailer4"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
          </div>

          <div class="closeDialog-btn">
            <v-btn color="error" block @click="dialog4 = false"> Close </v-btn>
          </div>
        </v-card>
      </v-dialog>
      <v-dialog
        class="dialog"
        v-model="dialog5"
        v-if="dialog5"
        fullscreen
        overlay-opacity="10"
      >
        <v-card height="100%" class="cardDialog">
          <div class="row videoDialog">
            <v-sheet
              color="error"
              width="100%"
              height="100%"
              dark
              class="pa-5"
              v-if="movieError5.length != 0"
            >
              <h1 class="video-error">{{ movieError5 }}</h1>
            </v-sheet>

            <iframe
              width="350"
              height="900"
              class="video"
              :src="trailer5"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
          </div>

          <div class="closeDialog-btn">
            <v-btn color="error" block @click="dialog5 = false"> Close </v-btn>
          </div>
        </v-card>
      </v-dialog>
      <v-dialog
        class="dialog"
        v-model="dialog6"
        v-if="dialog6"
        fullscreen
        overlay-opacity="10"
      >
        <v-card height="100%" class="cardDialog">
          <div class="row videoDialog">
            <v-sheet
              color="error"
              width="100%"
              height="100%"
              dark
              class="pa-5"
              v-if="movieError6.length != 0"
            >
              <h1 class="video-error">{{ movieError6 }}</h1>
            </v-sheet>

            <iframe
              width="350"
              height="900"
              class="video"
              :src="trailer6"
              frameborder="0"
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
            ></iframe>
          </div>

          <div class="closeDialog-btn">
            <v-btn color="error" block @click="dialog6 = false"> Close </v-btn>
          </div>
        </v-card>
      </v-dialog>
    </div>

    <v-sheet class="section-subtitle" elevation="10"
      >Check out the latest trailers</v-sheet
    >

    <div id="trailers-container">
      <div class="row no-gutters">
        <div class="col-lg-4">
          <v-card class="card">
            <img
              :src="url + movie1.poster_path"
              class="card-img"
              id="movie-img"
              @click="showDialog1()"
            />

            <h4 class="card-title" id="movie-title">{{ movie1.original_title }}</h4>
          </v-card>
        </div>
        <div class="col-lg-4">
          <v-card class="card">
            <img
              :src="url + movie2.poster_path"
              class="card-img"
              id="movie-img"
              @click="showDialog2()"
            />

            <h4 class="card-title" id="movie-title">{{ movie2.original_title }}</h4>
          </v-card>
        </div>

        <div class="col-lg-4">
          <v-card class="card">
            <img
              :src="url + movie3.poster_path"
              class="card-img"
              id="movie-img"
              @click="showDialog3()"
            />

            <h4 class="card-title" id="movie-title">{{ movie3.original_title }}</h4>
          </v-card>
        </div>
        <div class="col-lg-4">
          <v-card class="card">
            <img
              :src="url + movie4.poster_path"
              class="card-img"
              id="movie-img"
              @click="showDialog4()"
            />

            <h4 class="card-title" id="movie-title">{{ movie4.original_title }}</h4>
          </v-card>
        </div>

        <div class="col-lg-4">
          <v-card class="card">
            <img
              :src="url + movie5.poster_path"
              class="card-img"
              id="movie-img"
              @click="showDialog5()"
            />

            <h4 class="card-title" id="movie-title">{{ movie5.original_title }}</h4>
          </v-card>
        </div>
        <div class="col-lg-4">
          <v-card class="card">
            <img
              :src="url + movie6.poster_path"
              class="card-img"
              id="movie-img"
              @click="showDialog6()"
            />

            <h4 class="card-title" id="movie-title">{{ movie6.original_title }}</h4>
          </v-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SectionTitle from "../components/SectionTitle";
import { mapActions, mapState, getters } from "vuex";
import axios from "axios";

export default {
  name: "Trailers",
  components: {
    SectionTitle,
  },
  data() {
    return {
      name: "Trailers",
      url: "https://image.tmdb.org/t/p/original",
      video: "",
      movieTitle: "",
      videoDialog: "",
      dialog1: false,
      dialog2: false,
      dialog3: false,
      dialog4: false,
      dialog5: false,
      dialog6: false,
    };
  },
  computed: {
    ...mapState([
      "trailer1",
      "trailer2",
      "trailer3",
      "trailer4",
      "trailer5",
      "trailer6",
      "movie1",
      "movie2",
      "movie3",
      "movie4",
      "movie5",
      "movie6",
      "movieError1",
      "movieError2",
      "movieError3",
      "movieError4",
      "movieError5",
      "movieError6",
    ]),
  },
  methods: {
    ...mapActions(["getTrailers", "getMovies2020"]),

    showDialog1() {
      this.dialog1 = true;
    },
    showDialog2() {
      this.dialog2 = true;
    },
    showDialog3() {
      this.dialog3 = true;
    },
    showDialog4() {
      this.dialog4 = true;
    },
    showDialog5() {
      this.dialog5 = true;
    },
    showDialog6() {
      this.dialog6 = true;
    },
  },
  mounted() {
    this.getTrailers();
    this.getMovies2020();
  },
};
</script>

<style lang="scss">
@import "src/scss/variables";

// ******* MOBILE RESPONSIVE ******* //
@media only screen and (min-width: 360px) {
  #trailers-container {
    position: relative;
    margin: 0px;
    width: 100%;
    margin-bottom: 50px;
    height: 100%;
  }

  .card-title {
    text-align: center;
    font-weight: bold;
    color: $secondary;
    padding: 0px;
    font-size: 2em;
    letter-spacing: 5px;
    transition: 0.5s;
    display: hidden;
    opacity: 0;
  }

  .card-img {
    height: 100%;
  }

  .card-title {
    margin-bottom: -150px;
  }

  .card {
    margin: 0px;
    margin-bottom: 100px;
    width: 100%;
    overflow: hidden;
  }

  .videoDialog {
    margin: 0px;
    padding: 5px;
    overflow: hidden;
  }

  .closeDialog-btn {
    position: fixed;
    bottom: 0px;
    width: 100%;
    padding: 0px;
  }

  .video {
    height: 600px;
  }

  .cardDialog {
    position: fixed;
    bottom: 0px;
    width: 100%;
    height: 100%;
    z-index: 999999;
    background: $dark2 !important;
  }

  .video-error {
    font-size: 3em;
    text-align: center;
  }

  .section-subtitle {
    font-family: $style3;
    font-size: 2em;
    text-align: center;
    margin-bottom: 20px;
    letter-spacing: 4px;
    background: url("../assets/img/background4.jpg");
    background-repeat: repeat;
    color: $dark2 !important;
    text-shadow: 0px 0px 10px rgb(255, 255, 255);
    animation: move 2s ease-in-out;
  }

  .dialog {
    position: fixed;
    bottom: 0px;
    height: 100%;
  }
}
// ******* LAPTOP RESPONSIVE ******* //
@media only screen and (min-width: 767px) {
  #trailers-container {
    position: relative;
    margin: 0 auto;
    width: 90%;
    margin-bottom: 50px;
    height: 100%;
  }

  .card-title {
    text-align: center;
    font-weight: bold;
    color: $secondary;
    padding: 0px;
    font-size: 2em;
    letter-spacing: 5px;
    transition: 0.5s;
    display: hidden;
    opacity: 0;
  }

  .card-img {
    width: 100%;
    height: 600px;
    &:hover {
      cursor: pointer;
      transform: scale(1.2);
      transition: 1s;
      margin-bottom: 90px;
    }
  }

  .card-title {
    margin-bottom: -80px;
  }

  .card {
    margin: 5px;
    margin-bottom: 20px;
    width: 90%;
    overflow: hidden;

    &:hover {
      .card-title {
        display: block;
        opacity: 1;
        margin-bottom: 20px;
      }
    }
  }

  .videoDialog {
    margin: 0px;
    padding: 30px;
  }

  .closeDialog-btn {
    position: absolute;
    bottom: 0px;
    width: 100%;
    padding: 0px;
  }

  .video {
    height: 600px;
    position: absolute;
    left: 0px;
    top: 0px;
    margin: 0 auto;
  }

  .cardDialog {
    position: fixed;
    bottom: 0px;
    width: 100%;
    height: 100%;
    z-index: 999999;
    background: $dark2 !important;
  }

  .video-error {
    font-size: 3em;
    text-align: center;
  }

  .section-subtitle {
    font-family: $style3;
    font-size: 2em;
    text-align: center;
    margin-bottom: 20px;
    letter-spacing: 4px;
    background: url("../assets/img/background4.jpg");
    background-repeat: repeat;
    color: $dark2 !important;
    text-shadow: 0px 0px 10px rgb(255, 255, 255);
    animation: move 2s ease-in-out;
  }

  .dialog {
    position: fixed;
    bottom: 0px;
    height: 100%;
  }

  @keyframes move {
    from {
      margin-left: -5000px;
      opacity: 0;
    }
    to {
      margin-left: 0px;
      opacity: 1;
    }
  }
}

// ******* DESKTOP RESPONSIVE ******* //
@media only screen and (min-width: 1370px) {
  #trailers-container {
    position: relative;
    margin: 0 auto;
    width: 90%;
    margin-bottom: 50px;
    height: 100%;
  }

  .card-title {
    text-align: center;
    font-weight: bold;
    color: $secondary;
    padding: 0px;
    font-size: 2em;
    letter-spacing: 5px;
    transition: 0.5s;
    display: hidden;
    opacity: 0;
  }

  .card-img {
    width: 100%;
    height: 750px;
    &:hover {
      cursor: pointer;
      transform: scale(1.2);
      transition: 1s;
      margin-bottom: 90px;
    }
  }

  .card-title {
    margin-bottom: -150px;
  }

  .card {
    margin: 5px;
    margin-bottom: 20px;
    width: 90%;
    overflow: hidden;

    &:hover {
      .card-title {
        display: block;
        opacity: 1;
        margin-bottom: 20px;
      }
    }
  }

  .videoDialog {
    margin: 0px;
    padding: 20px;
    overflow: hidden;
  }

  .closeDialog-btn {
    position: absolute;
    bottom: 0px;
    width: 100%;
    padding: 0px;
  }

  .video {
    height: 900px;
  }

  .cardDialog {
    position: absolute;
    bottom: 0px;
    width: 100%;
    height: 100%;
    z-index: 999999;
    background: $dark2 !important;
  }

  .video-error {
    font-size: 3em;
    text-align: center;
  }

  .section-subtitle {
    font-family: $style3;
    font-size: 2em;
    text-align: center;
    margin-bottom: 20px;
    letter-spacing: 4px;
    background: url("../assets/img/background4.jpg");
    background-repeat: repeat;
    color: $dark2 !important;
    text-shadow: 0px 0px 10px rgb(255, 255, 255);
    animation: move 2s ease-in-out;
  }

  .dialog {
    position: absolute;
    bottom: 0px;
    height: 100%;
  }

  @keyframes move {
    from {
      margin-left: -5000px;
      opacity: 0;
    }
    to {
      margin-left: 0px;
      opacity: 1;
    }
  }
}
</style>