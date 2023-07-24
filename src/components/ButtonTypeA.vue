<template>
    <button 
        @click="btnFunction"
        :aria-label="btnAriaLabel"
        :class="[btnClass]">
            {{ btnName }}
    </button>
</template>

<script setup>   
    const props = defineProps({
        btnName: { 
            type: String,
            required: true,
        },
        btnClass: {
            type: Array,
            required: true,
        },
        btnAriaLabel: {
            type: String,
            required: true
        },
        btnFunction: {
            type: Function,
            required: true
        }
    })
</script>