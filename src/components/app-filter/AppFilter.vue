<template>
  <div class="btn-group">
    <PrimaryButton
      v-for="btn in filterButtons"
      :key="btn.name"
      :class="[filterName === btn.name ? 'btn-dark' : 'btn-outline-dark']"
      @click="filterHender(btn.name)"
    >
      {{ btn.title }}
    </PrimaryButton>
  </div>
</template>
<script>

export default {
  props: {
    updateFilterHender: {
      type: Function,
      required: true,
    },
    filterName: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      filterButtons: [
        {
          title: "Barcha kinolar",
          name: "all",
        },
        {
          title: "Mashxur kinolar",
          name: "popular",
        },
        {
          title: "Eng ko'p ko'rilgan kinolar",
          name: "mostViewers",
        },
      ],
      filter: "all",
    };
  },
  methods: {
    filterHender(filter) {
      this.filter = filter;
      this.updateFilterHender(this.filter);
    },
  },
};
</script>
<style scoped></style>
