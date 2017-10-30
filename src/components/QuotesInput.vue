<template>
 <div class="row">
   <div class="col-xs-12 col-lg-6 center-col">
     <h2 class="h4"><b>Quote</b></h2>
     <textarea maxlength="50" @keyup.enter="getQuote" v-model="singleQuote" type="text" placeholder="Enter your quote here..."></textarea>
     <div style="text-align: center; margin-top:20px;">
       <button @click="getQuote" class="btn">Add Quote</button>
     </div>
   </div>

 </div>
</template>

<script>
import {eventBus} from './../main'

export default {
  data: function() {
    return {
      singleQuote: '',
      quotesArr: []
    }
  },
   methods: {
    getQuote(){
      if(this.quotesArr.length >= 10) {
        return alert('You alredy added maximum allowed quotes. Please remove a quote to add a new one');
      }

      if(this.singleQuote == false){
        return false;
      }

      this.quotesArr.push(this.singleQuote);
      this.singleQuote = '';
      eventBus.$emit('quotesAmount', this.quotesArr);
    }
  }
}
</script>

<style scoped>
  .center-col{
    margin: 0 auto;
    float: none;
  }

  textarea {
    width: 100%;
    border-radius: 5px;
    height: 100px;
  }

</style>
