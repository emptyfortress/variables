<template lang="pug">
q-page(:style-fn="myTweak" padding)
	p(v-html="t('dialog.msg')")
	q-btn(label="Dialog" color="primary" @click="dialogVisible = true")

	q-dialog(v-model="dialogVisible" @hide="onHide")
		q-card
			q-card-section(class="row items-center q-pb-none")
				div(class="text-h6") Close icon
				q-space
				q-btn(v-close-popup icon="close" flat round dense)
			q-card-section  Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis perferendis totam, ea at omnis vel numquam exercitationem aut, natus minima, porro labore.
</template>

<script setup lang="ts">
	import { useI18n } from 'vue-i18n'
	import { ref } from 'vue'

	const { t, locale, availableLocales } = useI18n()
	let dialogVisible = ref(false)

	function onHide() {
		dialogVisible.value = false
	}
	const offset = 52
	const myTweak = () => {
		return { minHeight: offset ? `calc(100vh - ${offset}px)` : '100vh' }
	}
</script>

<style scoped lang="scss"></style>
