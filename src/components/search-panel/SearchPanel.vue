<template>
  <Input
    class="search-input"
    placeholder="kinolarni qidirish"
    v-model="term"
    @input="changeHender"
  />
</template>
<script>
export default {
  props: {
    updateTermHender: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      term: "",
    };
  },
  methods: {
    changeHender(e) {
      this.term = e.target.value;
      this.updateTermHender(this.term);
    },
  },
};
</script>
<style scoped>
.search-input {
  margin-top: 2rem;
  margin-bottom: 1rem;
  padding: 1.5rem;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
  background-color: #fcfaf5;
}
</style>
