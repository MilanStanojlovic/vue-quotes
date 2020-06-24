<template>
  <div class="row">
    <app-quote
      v-for="(quote, index) in quotes"
      :key="quote.quote"
      @click.native="deleteQuote(index)"
    >{{ quote }}</app-quote>
  </div>
</template>

<script>
import Quote from "./Quote";

export default {
  components: {
    "app-quote": Quote
  },

  props: ["quotes"],

  methods: {
    deleteQuote(index) {
      this.$emit("quoteDeleted", index);
    }
  }
};
</script>

<style scoped>
</style>