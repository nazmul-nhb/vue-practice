<script setup lang="ts">
import { computed, ref } from "vue";

// Define the emits type
const emit = defineEmits<{ (event: "dance", value: boolean): void }>();

// Use ref to make isDancing reactive
const isDancing = ref(false);

const buttonText = computed(() =>
	isDancing.value ? "Stop Dance" : "Start Dance"
);

// Create a computed property for button class
const buttonClass = computed(() => {
	const baseClass =
		"border px-6 py-2 text-xl font-bold rounded-full transition-all duration-500 hover:text-white";
	const colorClass = isDancing.value
		? "border-red-900 text-red-900 hover:bg-red-900"
		: "border-teal-900 text-teal-900 hover:bg-teal-900";
	return `${baseClass} ${colorClass}`;
});


// Handle dance button click
const handleDance = () => {
    isDancing.value = !isDancing.value; // Toggle dancing state
	emit("dance", isDancing.value); // Emit the dancing state
};
</script>

<template>
	<div class="w-full flex items-center justify-center">
		<button @click="handleDance" :class="buttonClass">
			{{ buttonText }}
		</button>
	</div>
</template>
