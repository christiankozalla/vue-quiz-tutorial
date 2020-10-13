<template>
  <div id="quiz-container">
    <img id="logo-crown" src="@/assets/crown.svg" alt="headsUP Crown" />
    <h1 id="logo-headline">headsUP</h1>
    <!-- div#correctAnswers -->
    <hr class="divider" />
    <div v-if="loading">Loading...</div>
    <div v-else v-html="questions[0].question">
      <!-- Only first Question is displayed -->
    </div>

    <hr class="divider" />
  </div>
</template>

<script>
export default {
  name: "Quiz",
  data() {
    return {
      questions: [],
      loading: true,
    };
  },
  methods: {
    async fetchQuestions() {
      this.loading = true;
      let response = await fetch(
        "https://opentdb.com/api.php?amount=10&category=9"
      );
      let jsonResponse = await response.json();
      let data = jsonResponse.results.map((question) => {
        // put answers on question into single array
        question.answers = [
          question.correct_answer,
          ...question.incorrect_answers,
        ];
        return question;
      });
      this.questions = data;
      this.loading = false;
    },
  },
  mounted() {
    this.fetchQuestions();
  },
};
</script>

<style scoped>
#quiz-container {
  margin: 1rem auto;
  padding: 1rem;
  max-width: 750px;
}

#logo-headline {
  font-size: 3rem;
  padding: 0.5rem;
  color: #f50057;
  text-align: center;
}

#logo-crown {
  display: block;
  width: 40%;
  margin: 0 auto;
}

@media only screen and (max-width: 500px) {
  #logo-crown {
    width: 30%;
  }

  #logo-headline {
    font-size: 1.8rem;
  }
}

h1 {
  font-size: 1.3rem;
  padding: 0.7rem;
}

.divider {
  margin: 0.5rem 0;
  border: 3px solid rgba(102, 255, 166, 0.7);
  border-radius: 2px;
  box-shadow: 3px 5px 5px rgba(0, 0, 0, 0.3);
}
</style>
