<template>
  <div id="app">
    <h1>Sentence Sentiment Analyzer</h1>
    <div class="input-container">
      <div><textarea v-model="sentence" placeholder="Type your sentence here..." rows="2" @keyup.enter="analyzeSentiment"></textarea></div>
      <div><button @click="analyzeSentiment">Analyze Sentiment</button></div>
    </div>
    <div v-if="feedback" class="feedback">
      <h3>Sentiment Feedback:</h3>
      <p :class="feedbackClass">{{ feedback }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sentence: '',
      feedback: '',
      sentiment: 'neutral'
    };
  },
  computed: {
    feedbackClass() {
      return {
        positive: this.sentiment === 'positive',
        negative: this.sentiment === 'negative',
        neutral: this.sentiment === 'neutral'
      }
    }
  },
  methods: {
    analyzeSentiment() {
      if (this.sentence.trim()) {
        if (this.sentence.includes('happy') || this.sentence.includes('good')) {
          this.feedback = 'Positive!';
          this.sentiment = 'positive';
        } else if (this.sentence.includes('sad') || this.sentence.includes('bad')) {
          this.feedback = 'Negative!';
          this.sentiment = 'negative';
        } else {
          this.feedback = 'Neutral!';
          this.sentiment = 'neutral';
        }
      } else {
        this.feedback = 'Please enter a valid sentence.';
        this.sentiment = 'neutral';
      }
    }
  }
};
</script>

<style scoped>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: black;
  color: beige;
  text-align: center;
  display: flex;
  flex-direction: column;
  padding: 15px; /* Adds padding for mobile screens */
  max-width: 960px;
  /* width: 100%; */
  margin: auto;
}

h1 {
  font-size: 24px; /* Responsive font size */
  margin-bottom: 20px;
}

.input-container {
  margin-bottom: 20px;
  /* display: block; */
}

textarea {
  width: 100%;
  max-width: 600px; /* Makes sure it doesn't get too wide */
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
  color: grey;
}

.feedback p {
  font-size: 18px;
}

.positive {
  color: lightgreen;
}

.negative {
  color: lightcoral;
}

.neutral {
  color: beige;
}


/* Mobile-First Design */
@media (min-width: 600px) {
  h1 {
    font-size: 28px;
  }
  
  button {
    max-width: 200px;
  }
}

</style>
