<template>
  <div class="container">
    <h1>Hello Toshkent {{ counter }}</h1>
    <button @click="onIncreament" class="btn btn-success">add</button>
    <button @click="onDecreament " class="btn btn-danger">delete</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 1,
    };
  },
  methods: {
    onIncreament() {
      this.counter += 1;
    },
    onDecreament() {
      this.counter -= 1;
    },
  },
};
</script>
