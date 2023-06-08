<template>
  <Box class="movie-add-form">
    <h3>Yangi kino qo'shish</h3>
    <form class="add-form d-flex" @submit.prevent>
      <Input
        type="text"
        class="form-control new-movie-lebal"
        placeholder="Qanday kino?"
        v-model="name"
      />
      <Input
        type="number"
        class="form-control new-movie-lebal"
        placeholder="Nechi marotaba ko'rilgan?"
        v-model="viewers"
      />
      <PrimaryButton class="btn-outline-dark" type="submit" @click="addMovie">
        Qo'shish
      </PrimaryButton>
    </form>
  </Box>
</template>
<script>

export default {
    data() {
        return {
            name: "",
            viewers: "",
        };
    },
    methods: {
        addMovie() {
            if (!this.viewers || !this.name)
                return;
            const newMovie = {
                name: this.name,
                viewers: this.viewers,
                favourite: false,
                like: false,
                id: Date.now(),
            };
            this.$emit("createMovie", newMovie);
            this.name = "";
            this.viewers = "";
        },
    },
};
</script>
<style>
.movie-add-form {
  margin-top: 2rem;
}
</style>
