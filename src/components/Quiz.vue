<template>
  <div id="quiz-container">
    <img id="logo-crown" src="@/assets/crown.svg" alt="headsUP Crown" />
    <h1 id="logo-headline">headsUP</h1>
    <hr class="divider" />
    <!-- question div -->
    Questions HTML here
    <hr class="divider" />
  </div>
</template>

<script>
export default {
  name: "Quiz",
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
