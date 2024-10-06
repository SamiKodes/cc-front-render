<template>
  <div id="app">
    <h1>Sentence Sentiment Analyzer</h1>
    <div class="input-container">
      <textarea v-model="sentence" placeholder="Type your sentence here..." rows="4"></textarea>
      <button @click="analyzeSentiment">Analyze Sentiment</button>
    </div>
    <div v-if="feedback" class="feedback">
      <h3>Sentiment Feedback:</h3>
      <p>{{ feedback }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sentence: '',
      feedback: ''
    };
  },
  methods: {
    analyzeSentiment() {
      if (this.sentence.trim()) {
        if (this.sentence.includes('happy') || this.sentence.includes('good')) {
          this.feedback = 'Positive sentiment detected!';
        } else if (this.sentence.includes('sad') || this.sentence.includes('bad')) {
          this.feedback = 'Negative sentiment detected!';
        } else {
          this.feedback = 'Neutral sentiment detected!';
        }
      } else {
        this.feedback = 'Please enter a valid sentence.';
      }
    }
  }
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
  padding: 0 15px; /* Adds padding for mobile screens */
}

h1 {
  font-size: 24px; /* Responsive font size */
  margin-bottom: 20px;
}

.input-container {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

textarea {
  width: 100%;
  max-width: 400px; /* Makes sure it doesn't get too wide */
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box; /* Ensure padding doesn’t mess up width */
}

button {
  width: 100%;
  max-width: 200px;
  padding: 10px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
  margin-top: 10px;
}

button:hover {
  background-color: #2c8a6e;
}

.feedback {
  margin-top: 20px;
}

.feedback h3 {
  color: #42b983;
}

.feedback p {
  font-size: 18px;
}

/* Mobile-First Design */
@media (min-width: 600px) {
  h1 {
    font-size: 28px;
  }

  button {
    max-width: 150px;
  }
}
</style>
