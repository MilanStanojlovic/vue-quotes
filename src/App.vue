<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-newQuote @quoteAdded="newQuote"></app-newQuote>
    <app-quoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quoteGrid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a quote to delete it</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid";
import NewQuote from "./components/NewQuote";
import Header from "./components/Header";

export default {
  components: {
    "app-quoteGrid": QuoteGrid,
    "app-newQuote": NewQuote,
    "app-header": Header
  },

  data: () => {
    return {
      quotes: ["Just a quote to see"],
      maxQuotes: 10
    };
  },

  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("Please delete quotes first.");
      }
      this.quotes.push(quote);
    },

    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style>
</style>