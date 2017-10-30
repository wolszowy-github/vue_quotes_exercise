<template>
  <div class="row">
    <div class="col-xs-12">
      <h1 class="h2"><b>Quotes Added</b></h1>
      <div class="app-progress-line">
        <div :style="{'width': barWidth}" class="app-progress-bar">
          <span class="quotes-count"><strong>{{ addedQuotes }} / {{ maxQuotes }}</strong></span>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
  import {eventBus} from './../main'

  export default {
    data: function(){
      return {
        addedQuotes: 0,
        maxQuotes: 10,
        barWidth: 0
      }
    },
    methods: {
      updatProgressBar(){
        this.barWidth = Math.round((this.addedQuotes / this.maxQuotes) * 100) + '%';
      }
    },
    created(){
      eventBus.$on('quotesAmount', (quotesArray) => {
        this.addedQuotes = quotesArray.length;
        this.updatProgressBar();
      });

      eventBus.$on('listUpdate', (quotesArray) => {
        this.addedQuotes = quotesArray.length;
        this.updatProgressBar();
      })
    }
  }
</script>

<style scoped>

  .app-progress-line{
    border-radius: 5px;
    width: 100%;
    height: 20px;
    overflow: hidden;
    box-shadow: inset 0px 0px 22px -8px rgba(0,0,0,0.75);
    background-color: rgba(149, 149, 149, 0.16);
  }

  .app-progress-bar{
    background-color: blue;
    text-align: center;
    color: #fff;
    transition: width .6s ease;
  }

  .quotes-count{
    display: inline-block;
    min-width: 50px;
  }

</style>
