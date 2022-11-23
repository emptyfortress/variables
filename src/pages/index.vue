<template lang="pug">
.column.flex-center.pa-4
	img(src="/src/assets/img/logo1.png" width="200")
	HelloWorld(msg="This is message")
	span.text-accent 22
	span {{ count }}
	AsyncInput(v-model="count")
</template>

<script setup lang="ts">
	import HelloWorld from 'src/components/HelloWorld.vue'
	import { defineAsyncComponent } from 'vue'
	import { ref } from 'vue'

	// import CustomInput from 'src/components/CustomInput.vue'
	//Async Components
	const AsyncInput = defineAsyncComponent(() => import('src/components/CustomInput.vue'))

	interface User {
		name: string
		age: number
	}

	const count = ref<string | null>(null)
</script>

<style lang="scss" scoped></style>
