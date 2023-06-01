<template>
  <li
    class="list-gruop-item d-flex justify-content-between"
    :class="[{ like: movie.like }, { favourite: movie.favourite }]"
  >
    <span class="list-gruop-item-lebal"> {{ movie.name }} </span>
    <input type="number" class="list-gruop-item-input" :value="movie.viewers" />
    <div class="d-flex justify-content-center align-item-center">
      <button type="button" class="btn-cookie btn-sm">
        <i class="fas fa-cookie"></i>
      </button>
      <button type="button" class="btn-trash btn-sm">
        <i class="fas fa-trash"></i>
      </button>
      <i class="fas fa-star"></i>
    </div>
  </li>
</template>
<script>
export default {
  props: {
    movie: {
      type: Object,
      required: true,
    },
  },
};
</script>
<style>
.list-gruop-item {
  padding: 15px 20px;
  border: none;
  border-bottom: 1px solid #3d5a80;
}
.list-gruop-item:last-child {
  border-bottom: none;
}
.list-gruop-item span {
  line-height: 35px;
  width: 550px;
  font-size: 20px;
  cursor: pointer;
}
.list-gruop-item input {
  line-height: 35px;
  font-size: 20px;
  align-items: center;
  border: none;
  outline: none;
}
.list-gruop-item button {
  width: 35px;
  height: 35px;
  margin: 3px;
  font-size: 17px;
  border: none;
  cursor: pointer;
}
.list-gruop-item .btn-cookie {
  color: #e89f3e;
}
.list-gruop-item .btn-trash {
  color: #e5383b;
}
.list-gruop-item .fa-star {
  width: 35px;
  height: 35px;
  color: #ffd700;
  align-items: center;
  line-height: 35px;
  font-size: 16px;
  transition: 0.3s all;
  transform: translateX(30px);
  opacity: 0;
}
.list-gruop-item.like .fa-star {
  transform: translateX(0px);
  opacity: 1;
}
.list-gruop-item.favourite .list-gruop-item-lebal,
.list-gruop-item.favourite .list-gruop-item-input {
  color: #e09f3e;
}
</style>
