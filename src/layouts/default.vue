<template lang="pug">
q-layout(view="hHh LpR fFf")
	q-header(bordered class="bg-grey text-white text-left")
		q-toolbar
			q-btn(dense flat round icon="menu" @click="toggleLeftDrawer")
			q-toolbar-title
				q-avatar
					img(src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg")
				|Title

	q-drawer(show-if-above v-model="leftDrawerOpen" side="left" width="350" bordered)
		q-list(bordered separator)
			template(v-for="(item, index) in generatedRoutes")
				q-item(clickable :key="index" v-if="item.name != 'index'" class="flex-col")
					q-item-section(class="cursor-pointer" @click="router.push({ path: item.path })") {{ item.name }}

	q-page-container
		router-view(v-slot="{ Component }")
			transition(name="slide-fade" mode="out-in")
				component(:is="Component")
</template>

<script setup lang="ts">
	import { ref } from 'vue'
	import { useRouter } from 'vue-router'

	import generatedRoutes from '~pages'
	const router = useRouter()

	const leftDrawerOpen = ref<boolean>(false)
	const toggleLeftDrawer = () => {
		leftDrawerOpen.value = !leftDrawerOpen.value
	}
</script>

<style lang="scss">
	.slide-fade-enter {
		transform: translateX(10px);
		opacity: 0;
	}

	.slide-fade-enter-active,
	.slide-fade-leave-active {
		transition: all 0.2s ease;
	}

	.slide-fade-leave-to {
		transform: translateX(-10px);
		opacity: 0;
	}
</style>
