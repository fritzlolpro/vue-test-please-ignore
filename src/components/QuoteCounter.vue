<template>
  <div>
    <h1>Quotes Added</h1>
    <Bar :progressLvl=quotesNumber></Bar>
  </div>
</template>

<script>
import Bar from "./Bar.vue";
export default {
	props: {
		quotesNumber: Number
	},
	components: {
		Bar
	}
};
</script>

<style scoped>
</style>