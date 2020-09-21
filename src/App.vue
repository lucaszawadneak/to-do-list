<template>
  <div id="app">
    <h1>Tarefas</h1>
    <progress-bar :value="progress" />
    <task-input @valueChange="newCard = $event" @submit="submitCard()" />
    <cards
      :data="cards"
      @handleChange="handleCardDone"
      @handleDelete="handleCardDelete"
    />
  </div>
</template>

<script>
import ProgressBar from "./components/ProgressBar";
import Input from "./components/Input";
import Cards from "./components/Cards";

export default {
  components: { ProgressBar, TaskInput: Input, Cards },
  data() {
    return {
      newCard: "",
      progress: 0,
      cards: [],
      completed: 0,
    };
  },
  methods: {
    changeText(e) {
      this.newCard = e.target.value;
    },
    handleProgressCalc() {
      this.progress = (
        (this.completed / (this.cards.length || 1)) *
        100
      ).toFixed(2);
    },
    submitCard() {
      this.cards.push({ title: this.newCard, done: false });
      this.newCard = "";
      this.handleProgressCalc();
    },
    handleCardDone(event) {
      this.completed++;
      this.handleProgressCalc();
      const index = this.cards.findIndex((item) => item.title === event);
      if (index >= 0) {
        this.cards[index].done = true;
      }
    },
    handleCardDelete(event) {
      const index = this.cards.findIndex((item) => item.title === event);
      if (index >= 0) {
        if (this.cards[index].done) {
          this.completed--;
        }
        this.cards.splice(index, 1);
      }
      this.handleProgressCalc();
    },
  },
};
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>
