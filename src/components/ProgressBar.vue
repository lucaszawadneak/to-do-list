<template>
  <div>
    <progress max="100" min="0" :value="value"> </progress>
    <span>{{ value }}%</span>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style scoped>
div {
  margin: 10px 0px;
  display: flex;
  align-items: center;
  flex-direction: column;
}
progress {
  -webkit-appearance: none;
  appearance: none;

  width: 500px;
  height: 30px;
}
progress::-webkit-progress-bar {
  background-color: transparent;
  border: 1px solid #fff;
  border-radius: 10px;
}
progress::-webkit-progress-value {
  border-radius: 10px;
  background-color: #62ba1a;
  transition: 300ms;
}
span {
  margin: 10px 0px;
}
</style>
