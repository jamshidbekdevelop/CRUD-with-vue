<template>
  <div class="app">
    <div class="content">
      <AppInfo
        :allMoviesCount="movies.length"
        :favouriteMoviesCount="movies.filter((c) => c.favourite).length"
      />
      <div class="search-info">
        <Searchpanel :updateTermHender="updateTermHender" />
        <AppFilter
          :updateFilterHender="updateFilterHender"
          :filterName="filter"
        />
      </div>
      <MovieList
        :movies="onFilterHender(onSearchHender(movies, term), filter)"
        @onToggle="onToggleHender"
        @onDelete="onDeleteHender"
      />
      <MovieAddForm @createMovie="createMovie" />
    </div>
  </div>
</template>

<script>
import AppInfo from "@/components/app-info/AppInfo.vue";
import Searchpanel from "@/components/search-panel/SearchPanel.vue";
import AppFilter from "@/components/app-filter/AppFilter.vue";
import MovieList from "@/components/movie-list/MovieList.vue";
import MovieAddForm from "@/components/movie-add-form/MovieAddForm.vue";
export default {
  components: {
    AppInfo,
    Searchpanel,
    AppFilter,
    MovieList,
    MovieAddForm,
  },
  data() {
    return {
      movies: [
        { id: 1, name: "Omar", viewers: 811, favourite: false, like: true },
        {
          id: 2,
          name: "Empire of osmon",
          viewers: 411,
          favourite: false,
          like: false,
        },
        { id: 3, name: "Ertugrul", viewers: 711, favourite: true, like: false },
      ],
      term: "",
      filter: "all",
    };
  },
  methods: {
    createMovie(item) {
      this.movies.push(item);
    },
    onToggleHender({ id, props }) {
      this.movies = this.movies.map((item) => {
        if (item.id == id) {
          return { ...item, [props]: !item[props] };
        }
        return item;
      });
    },
    onDeleteHender(id) {
      this.movies = this.movies.filter((item) => {
        return item.id !== id;
      });
    },
    onSearchHender(arr, term) {
      if (term.length == 0) {
        return arr;
      }
      return arr.filter((c) => c.name.toLowerCase().indexOf(term) > -1);
    },
    onFilterHender(arr, filter) {
      switch (filter) {
        case "popular":
          return arr.filter((c) => c.like);
        case "mostViewers":
          return arr.filter((c) => c.viewers > 500);
        default:
          return arr;
      }
    },
    updateTermHender(term) {
      this.term = term;
    },
    updateFilterHender(filter) {
      this.filter = filter;
    },
  },
};
</script>

<style>
.app {
  height: 100vh;
  color: #000;
}
.content {
  width: 1000px;
  min-height: 700px;
  background-color: #fff;
  margin: 0 auto;
  padding: 5rem 0;
}
.search-info {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>
