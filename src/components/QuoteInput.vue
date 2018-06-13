<template>
  <div>
    <div class="quote-input col-md-6 offset-md-3 ">
        <h3>Quote</h3>
        <div class="input-group">
          <textarea v-model="currentQuote" class="form-control" aria-label="With textarea"></textarea>
        </div>
        <button @click="addQuote(currentQuote)" class="btn btn-primary ">Add quote</button>
      </div>
  </div>
</template>

<script>
import { eventBus } from "../main.js";
export default {
	data() {
		return {
			currentQuote: ""
		};
	},
	methods: {
		addQuote(quote) {
			if (this.currentQuote.length < 1) {
				alert("empty strings forbidden");
				return false;
			}
			eventBus.$emit("quoteAdded", quote);
			this.currentQuote = "";
		}
	},
	watch: {
		//watch for each state update and emit it
		currentQuote(val) {
			eventBus.$emit("input", val);
		}
	}
};
</script>

<style scoped>
h3 {
	margin: 16px 0px;
}
button {
	margin: 16px 0px;
}
</style>