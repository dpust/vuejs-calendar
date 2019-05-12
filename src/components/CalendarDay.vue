<template>
	<div
	 :class="classObject"
	 @click="captureClick"
	>{{ day.format('D') }}</div>
</template>

<script>
export default {
	props: ['day'],
	computed: {
		classObject () {
			let Today = this.day.isSame(this.$moment(), 'day')
			return {
				day: true,
				today: Today,
				past: this.day.isSameOrBefore(this.$moment(), 'day') && !Today
			}
		}
	},
	methods: {
		captureClick (event) {
			this.$store.commit('eventFormPos', { x: event.clientX, y: event.clientY });
			this.$store.commit('eventFormActive', true);

		}
	}
}
</script>

</style>
