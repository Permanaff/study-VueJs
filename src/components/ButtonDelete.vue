<template>
    <button @click="$emit('onclick')">
        <slot/>
    </button>
</template>