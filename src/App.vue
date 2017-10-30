<template>
    <div class="container">
      <progress-bar></progress-bar>
      <quotes-input></quotes-input>
      <quotes-display></quotes-display>
    </div>
</template>

<script>
    import ProgressBar from './components/ProgressBar.vue';
    import QuotesInput from './components/QuotesInput.vue';
    import QuotesDisplay from './components/QuotesDisplay.vue';

    export default {
      components: {
        'progress-bar': ProgressBar,
        'quotes-input': QuotesInput,
        'quotes-display': QuotesDisplay
      }
    }
</script>

<style>

</style>
