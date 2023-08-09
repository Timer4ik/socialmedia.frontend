<template>
    <input :value="modelValue" @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)" />
</template>

<script setup lang="ts">
import { type InputHTMLAttributes, type ReservedProps } from "vue"

interface Props extends /* @vue-ignore */  InputHTMLAttributes {
    modelValue: string
}
defineProps<Props>()

interface Emits {
    (event: "update:modelValue"): void
}
defineEmits<Emits>()

</script>
