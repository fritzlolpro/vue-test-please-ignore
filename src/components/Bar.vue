<template>
  <div>
    <div class="progress" style="height: 20px;">
    <div class="progress-bar" role="progressbar" aria-valuenow="progressLvl" aria-valuemin="0" aria-valuemax="progressMax" :style="{width:barWidth + '%', color:barLabelColor}">{{ progressLvl }} / {{ progressMax }}</div>
    </div>
  </div>
</template>

<script>
export default {
	data() {
		return {
			progressMax: 10
		};
	},
	props: {
		progressLvl: {
			type: Number,
			default: 0
		}
	},
	computed: {
		barWidth() {
			return this.progressLvl * 10;
		},
		barLabelColor() {
			return this.barWidth === 0 ? "black" : "white";
		}
	}
};
</script>

<style scoped>
</style>