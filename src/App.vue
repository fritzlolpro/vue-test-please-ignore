<template>
    <div class="container">
      <QuoteCounter  :quotesNumber=quotesNumber></QuoteCounter>
      <QuoteInput></QuoteInput>
      <QuoteCountainer  v-for="(q, i) in quotes" :quote='q' :key="i" :id='i'  ></QuoteCountainer>
      <div class="alert alert-primary" role="alert">
        Click on plate to delete it
      </div>
    </div>
</template>

<script>
import { eventBus } from "./main.js";
import QuoteCounter from "./components/QuoteCounter.vue";
import QuoteInput from "./components/QuoteInput.vue";
import QuoteCountainer from "./components/QuoteCountainer.vue";
export default {
	components: {
		QuoteCounter,
		QuoteInput,
		QuoteCountainer
	},
	data() {
		return {
			currentQuote: "",
			quotes: []
		};
	},
	computed: {
		quotesNumber() {
			return this.quotes.length;
		}
	},
	methods: {},
	created() {
		// listen to input events and update state
		eventBus.$on("input", val => {
			this.currentQuote = val;
		});

		//btn bindings
		eventBus.$on("quoteAdded", quote => {
			if (this.quotes.length + 1 > 10) {
				alert("to many quotes delete some first");
				return false;
			} else {
				this.quotes.push(quote);
			}
		});

		eventBus.$on("deleteQuote", id => {
			this.quotes.splice(id, 1);
		});
	}
};
</script>

<style scoped>
.quote-input {
	margin-top: 60px;
}
</style>
