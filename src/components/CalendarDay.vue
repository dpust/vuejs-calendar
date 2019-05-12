<template>
	<div :class="classObject">{{ day.format('D') }}</div>
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
	}

}
</script>

</style>
