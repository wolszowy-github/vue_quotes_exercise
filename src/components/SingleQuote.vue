<template>
  <div @click="removeQuote" class="quote-box col-xs-6 col-lg-3">
        <span class="h1">{{quoteItem}}</span>
  </div>

</template>

<script>
import {eventBus} from './../main'

export default {
  props: ['quoteItem', 'quotesListPass', 'indexItem'],
  methods: {
    removeQuote(){
      this.quotesListPass.splice(this.indexItem, 1);
      eventBus.$emit('listUpdate', this.quotesListPass);
    }
  }
}
</script>

<style scoped>
  .quote-box {
    font-family: 'Arizonia';
    border: 1px solid lightgray;
    cursor: pointer;
    padding: 10px 10px;
    border-radius: 5px;
    height: 100%;
    word-break: break-all;
    transition: background-color .6s ease;
    max-height: 140px;
    min-height: 140px;
    overflow: hidden;
  }

  .quote-box:hover{
    background-color: rgba(195, 133, 189, 0.4);
  }
</style>
