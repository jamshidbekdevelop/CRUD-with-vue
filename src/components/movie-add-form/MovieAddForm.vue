<template>
  <div class="movie-add-form">
    <h3>Yangi kino qo'shish</h3>
    <form class="add-form d-flex">
      <input
        type="text"
        class="form-control new-movie-lebal"
        placeholder="Qanday kino?"
        :value="name"
        @input="name = $event.target.value"
      />
      <input
        type="text"
        class="form-control new-movie-lebal"
        placeholder="Nechi marotaba ko'rilgan?"
        :value="viewer"
        @input="viewer = $event.target.value"
      />
      <button class="btn btn-outline-dark" type="submit">Qo'shish</button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "",
      viewer: "",
    };
  },
};
</script>
<style>
.movie-add-form {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>
