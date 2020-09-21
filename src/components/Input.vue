<template>
  <div>
    <input placeholder="Nova tarefa" v-model="value" />
    <button @click="handleSubmit">+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: "",
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("submit");
      this.value = "";
    },
  },
  watch: {
    value() {
      this.$emit("valueChange", this.value);
    },
  },
};
</script>

<style scoped>
div {
  height: 30px;
}
button {
  outline: none;
  border: 0px;
  height: 30px;
  width: 30px;
  padding: 5px;
  background-color: #fff;
}
input {
  padding: 0px 5px;
  outline: none;
  border: 0px;
  height: 30px;
  width: 200px;
}
</style>
