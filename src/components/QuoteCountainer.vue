<template>
  <div class="card" @click="deleteQuote(id)">
      <div class="card-body">
        <p class="card-text">{{quote}}</p>
      </div>
  </div>
</template>

<script>
import { eventBus } from "../main.js";
export default {
	props: ["quote", "id"],
	methods: {
		deleteQuote(id) {
			eventBus.$emit("deleteQuote", id);
		}
	}
};
</script>

<style scoped>
.card {
	cursor: pointer;
	margin-bottom: 20px;
	margin-top: 20px;
}
</style>