<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <new-quote @quoteAdded="newQuote"></new-quote>
    <quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on Quote to delete it.</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";
export default {
  data: function() {
    return {
      quotes: ["Just a quote."],
      maxQuotes: 10
    };
  },
  components: {
    quoteGrid: QuoteGrid,
    newQuote: NewQuote,
    appHeader: Header
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        alert("Please delete some quotes first");
      } else {
        this.quotes.push(quote);
      }
    },
    deleteQuote(index) {
      debugger;
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style>
</style>
