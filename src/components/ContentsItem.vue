<template>
	<li>
		<p v-if="item.skipped" class="contents_item skipped">{{item.text}}</p>
		<p v-else class="contents_item">{{item.text}}</p>
	</li>
</template>

<script>
export default {
  props: {
    item: {
			no: 0,
			text: "",
			skipped: false
    }
  }
}
</script>

<style scoped>
.contents_item {
	border: 1px solid lightgray;
	border-radius: 5px;
	margin: 0.2em 0;
	padding: 0.5em;
}
.skipped {
  background-color: lightgray;
	color: gray;
}
</style>
