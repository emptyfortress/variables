<template>
	<div ref="contentRef" class="min-h-100vh bg-slate-300 text-center">laksd</div>
</template>

<script setup>
	import { ref, onMounted } from 'vue'
	import { useEventListener } from 'src/composables'

	const contentRef = ref(null)

	//   useEventListener(contentRef.value, )
	onMounted(() => {
		useEventListener(contentRef.value, 'scroll', () => {
			console.log(13)
		})
	})
</script>

<style lang="less" scoped></style>
