<template>
  <div style="margin-top: 20px;" class="row">
    <single-quote v-for="(quote, index) in quotesList" :quotesListPass="quotesList" :indexItem="index" :quoteItem="quote"></single-quote>
    <div class="col-xs-12 info-box">
      <p class="text-center">Info: click on a quote to delete it from the list</p>
    </div>
  </div>


</template>

<script>
import SingleQuote from './SingleQuote.vue'
import {eventBus} from './../main'

export default {
  components: {
    'single-quote': SingleQuote
  },
  data: function(){
    return {
      quotesList: []
    }
  },
  created(){
    eventBus.$on('quotesAmount', (quotesArray) => {
      this.quotesList = quotesArray;
    })
  }
}
</script>

<style scoped>
  .info-box{
    background-color: lightblue;
    padding: 30px;
    margin-top: 20px;
    border-radius: 5px;
  }

  p {
    margin: 0;
  }
</style>
