<template>
  <div id="app">
    <Header
      :numCorrect="numCorrect"
      :numTotal="numTotal"
    />
    <b-container class="bv-example-row">
      <b-row>
          <b-col small="6" offset="3">
            <QuestionAnswer 
              v-if="questions.length"
              :currentQuestion="questions[index]"
              :next="next"
              :increment="increment"
            />
          </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import QuestionAnswer from './components/QuestionAnswer.vue'

export default {
  name: 'app',
  components: {
    Header,
    QuestionAnswer
  },
  data(){
    return{
      questions: [],
      index: 0,
      numCorrect: 0,
      numTotal: 0
    }
  },
  methods: {
    next() {
      this.index++
    },
    increment(isCorrect) {
      if(isCorrect){
        this.numCorrect++
      }
      this.numTotal++
    }
  },
  mounted: function(){
    fetch('https://opentdb.com/api.php?amount=10&category=21&difficulty=easy', {
      method: 'get'
    })
      .then((response) => {
        return response.json()
      })
      .then((jsonData) => {
        this.questions = jsonData.results
      })
  }
}
</script>