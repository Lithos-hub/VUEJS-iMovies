# iMovies

iMovies is a web app I'm developing using Vue. 

This application uses The Movie Database (TMDB) API to show info about movies (release dates, titles, vote average, overviews, etc).

The app is divided into some sections that can be accesible by the expandible side menu:

* Famous current movies (Trending).
* The latest available movie trailers (Trailers);
* Movies classified by genres and popularity (Genres);
* And a popular movies classification by year, from 2010 to 2020.

In some of those sections you may get or access certain info with buttons that trigger a modal window.

In the future, I'll add new features like the posibility to create want-to-watch movie lists or a search system to filter movies with names of actores, genres, or years of release.

//////////////

Changelog:

Version 1.1
* Added dynamic routes on main page when you click over a movie image to get details about that movie.


Version 1.2
* Added dynamic trailers dialogs on /movie/id page.
* Added some aesthetic changes on /trailers page.

Version 1.3

* Optimized code in the Genres section using v-bind and v-on:click to use a single function to return movies of different genres.
* Some aesthetic changes in general.

Version 1.4

* New features in Trending section.
* Optimized code in Ranking section.
* New responsive features in Ranking section and some aesthetic changes.

Version 1.5

* Added My Movies section
* Added new features (Watched, Favourite, Rate and To-Watch) in Ranking section
* Now you can create your custom movie lists with those categories and find them in My Movies section. 

Version 1.6

* Optimized code in Trailers section.
* General aesthetic improvements.
* Info button available in My Movies section.
* Now is possible to save the user rates for each movie in My Movies.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
