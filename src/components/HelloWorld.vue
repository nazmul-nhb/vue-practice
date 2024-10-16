<script setup lang="ts">
import Dance from "./Dance.vue";
import { ref } from "vue";

defineProps<{ heading: string }>();

const dancingClass = ref("");

const updateDanceState = (isDancing: boolean) => {
	dancingClass.value = isDancing ? "animate-bounce" : "animate-none";
};

console.log(dancingClass);
</script>

<template>
	<h1
		:class="`h-[33vh] text-3xl font-bold flex items-center justify-center ${dancingClass}`"
	>
		{{ heading }}
	</h1>
	<Dance @dance="updateDanceState" />
</template>
