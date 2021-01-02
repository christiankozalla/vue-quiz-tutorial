<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <h2>{{ header }}</h2>
            <h3>{{ subheader }}</h3>
          </div>

          <div class="modal-body">
            <div id="score">
              You answered
              <span class="highlight">
                {{
                  Math.floor(
                    (quizScore.correctlyAnsweredQuestions /
                      quizScore.allQuestions) *
                      100
                  )
                }}
                % correctly!
              </span>
              Answered
              <span class="highlight">
                {{ quizScore.correctlyAnsweredQuestions }} out of
                {{ quizScore.answeredQuestions }}
              </span>
              questions.
            </div>
            <div id="chooseCategory">
              Wanna choose another category?

              <a
                href="https://twitter.com/messages/compose?recipient_id=1315961855148523521&text=Hello%20Christian%20I%20would%20like%20to%20choose%20other%20categories%20with%20headsUP"
                class="twitter-dm-button"
                data-screen-name="@CKozalla"
              >
                <img
                  src="@/assets/Twitter_Logo_WhiteOnBlue.png"
                  alt="Twitter Logo"
                  class="twitter-logo"
                />Demand that feature!
              </a>
            </div>
          </div>

          <div class="modal-footer">
            <button
              id="play-again"
              class="button-footer"
              @click="$emit('reload')"
            >
              Play Again
            </button>
            <button
              id="close-button"
              class="button-footer"
              @click="$emit('close')"
            >
              Close
            </button>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "Modal",
  props: {
    header: String,
    subheader: String,
    quizScore: Object,
  },
};
</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 90vw;
  max-width: 650px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 6px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-header {
  text-align: center;
}

.modal-header h2 {
  color: rgb(0, 178, 72);
}

.modal-header h3 {
  color: rgb(0, 178, 72);
}

.modal-body {
  display: flex;
  flex-direction: column;
  margin: 20px 0;
  line-height: 3rem;
}

.modal-body > * {
  margin: 1rem 0;
  padding: 0.25rem 0.5rem;
}

.modal-footer {
  display: flex;
  justify-content: space-between;
}

.button-footer {
  padding: 1rem 2rem;
  background: linear-gradient(
    210deg,
    rgba(187, 0, 47, 0.8),
    rgba(245, 0, 87, 0.6)
  );
  border-radius: 7px;
  border: none;
}

.anchor-footer {
  color: black;
  text-decoration: none;
  cursor: default;
}

.button-footer:active,
.button-footer:focus {
  outline: none;
}

.button-footer:hover {
  transform: scale(1.02);
}

.highlight {
  border-radius: 4px;
  background-color: rgba(187, 0, 47, 0.3);
  padding: 0.25rem 0.5rem;
}

.twitter-dm-button {
  display: flex;
  justify-content: space-between;
  width: 280px;
  background-color: #1da1f2;
  padding: 0 2rem;
  border-radius: 7px;
  text-decoration: none;
  color: black;
  margin: 0 auto;
}

.twitter-logo {
  width: 48px;
  height: 48px;
}

#score {
  background-color: rgb(210, 200, 200);
  border-radius: 5px;
  box-shadow: 2px 3px 9px gray;
}

#chooseCategory {
  text-align: center;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>
