<script lang="ts" setup>
import PlayingCard from '@/components/PlayingCard.vue';
</script>

<template>
    <div class="game-board">
        <div class="empty-space"/>
        <div class="cards-wrapper">
            <playing-card card-value="Q" suit="heart"/>
            <playing-card card-value="6" suit="spade"/>    
            <playing-card card-value="K" suit="club"/>
        </div>
    </div>
</template>

<style>
.game-board {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
}

.cards-wrapper {
    display: flex;
    gap: 20px;   
}

.empty-space {
    height: 20rem;
    width: 12rem;
}
</style>