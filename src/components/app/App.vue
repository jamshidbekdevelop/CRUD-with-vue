<template>
  <div class="app">
    <div class="content">
      <AppInfo
        :allMoviesCount="movies.length"
        :favouriteMoviesCount="movies.filter((c) => c.favourite).length"
      />
      <div class="search-info">
        <Searchpanel />
        <AppFilter />
      </div>
      <MovieList :movies="movies" />
      <MovieAddForm />
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
        { name: "Omar", viewers: 811, favourite: false, like: true },
        {
          name: "Empire of osmon",
          viewers: 411,
          favourite: false,
          like: false,
        },
        { name: "Ertugrul", viewers: 711, favourite: true, like: false },
      ],
    };
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
