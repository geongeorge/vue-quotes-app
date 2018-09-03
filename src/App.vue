<template>
  <div class="container" id="app">
    <h1 class="title is-1">Quotes App</h1>
    <progress class="progress is-warning" :value="getPer()" max="100">{{getPer()}}%</progress>
    <br>
    <quote-input placeholder="Enter Quote here..." @entered="addQuote"></quote-input>
    <quotes-list>
      <transition-group name="slide-fade">
        <single-quote v-for="(q,i) in quotes" :key="i">{{q}}</single-quote>
      </transition-group>
    </quotes-list>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import InputText from './components/InputText.vue'
import QuotesList from './components/QuotesList.vue'
import SingleQuote from './components/SingleQuote.vue'

export default {
  name: 'app',
  components: {
    "quotes-list": QuotesList ,
    "single-quote": SingleQuote,
    "quote-input" : InputText
  },
  data: function() {
    return {
      quotes: [],
      quotelength:0,
      quoteMaxLength:10
    }
  },
  methods : {
    addQuote(event) {
      this.quotes.push(event)
      this.quotelength++
    },
    getPer() {
      return this.quotelength*10
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 400px;
}

progress::-webkit-progress-value {
  transition:width 0.3s linear
}

/* Enter and leave animations can use different */
/* durations and timing functions.              */
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
</style>
