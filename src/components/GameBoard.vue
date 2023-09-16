<script lang="ts" setup>
import PlayingCard from '@/components/PlayingCard.vue';
</script>

<template>
    <div class="game-board">
        <playing-card card-value="Q" suit="heart"/>
        <playing-card card-value="6" suit="spade"/>    
        <playing-card card-value="K" suit="club"/>
    </div>
</template>