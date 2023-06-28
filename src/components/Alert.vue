<script setup>
 const props = defineProps({
    alert:{
        type: Object,
        required: true
    }
 })
</script>

<template>
    <div
        class=" text-white text-center p-3 font-bold mb-3 rounded-md bg-red-500">
        {{ alert.message }}
    </div>
</template>