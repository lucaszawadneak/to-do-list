<template>
  <div class="holder">
    <template v-for="item in data">
      <div
        :key="item.title"
        :class="{ card: true, active: !item.done, finished: item.done }"
      >
        <button
          @click="handleDelete(item.title)"
          :class="{ activeButton: !item.done, finishedButton: item.done }"
        >
          X
        </button>
        <p @click="handleStatusChange(item.title)">{{ item.title }}</p>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      required: true,
    },
  },
  methods: {
    handleStatusChange(key) {
      this.$emit("handleChange", key);
    },
    handleDelete(key) {
      this.$emit("handleDelete", key);
    },
  },
};
</script>

<style scoped>
.holder {
  width: 80%;
  display: flex;
  flex-wrap: wrap;
  max-height: 200px;
  align-items: center;
  justify-content: center;
  margin: 20px 0px;
}

.card {
  height: 100px;
  width: 200px;
  background-color: #62ba1a;
  margin: 5px;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  transition: 300ms;
}
.card > p {
  cursor: pointer;
}

.card > button {
  position: absolute;
  top: 0;
  right: 0;
  margin: 5px;
  outline: none;
  border: 0px;
  height: 20px;
  width: 20px;
  border-radius: 15px;
  transition: 300ms;
  color: #fff;
  cursor: pointer;
  font-size: 10px;
}

.active {
  background-color: #62ba1a;
}
.finished {
  background-color: #d40d52;
  text-decoration: line-through;
}

.activeButton {
  background-color: #4ea368;
}
.finishedButton {
  background-color: #8f0725;
}
</style>
