<script lang="ts" setup>
import { ref } from 'vue';

import PlayingCard from '@/components/PlayingCard.vue';

let isAnimationActive = ref(false);
</script>

<template>
    <div class="game-board">
        <div class="empty-space"/>
        <div class="cards-wrapper">
            <playing-card card-value="Q" suit="heart"/>
            <playing-card :class="{active: isAnimationActive}" card-value="6" suit="spade"/>    
            <playing-card card-value="K" suit="club"/>
        </div>
        <div class="button-wrapper">
            <button @click="isAnimationActive=!isAnimationActive">{{isAnimationActive ? 'RESET' : 'START'}}</button>
        </div>
    </div>
</template>

<style>
.game-board {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--gap-m);
    position: relative;
}

.cards-wrapper {
    display: flex;
    gap: var(--gap-m);   
}

.empty-space {
    height: 20rem;
    width: 12rem;
}

button {
    background-color: unset;
    border: 1px solid var(--secondary-color);
    padding: var(--btn-padding);
    color: var(--secondary-color);
    cursor: pointer;
    font-weight: bolder;
}

button:active {
    color: var(--main-color);
    background-color: var(--secondary-color); 
}

.active {
    transform-style: preserve-3d;
    animation: moveCard 5s;
    animation-fill-mode: forwards;
    z-index: 1;
}

@keyframes moveCard {
    20% {
        transform: translateX(-20%);
    }
    30% {
        transform: translateX(0) rotate3d(0,1,0,180deg) ;
        scale: 1;
    }
    50% {
        scale: 1.3;
    }
    100% {
        transform: translateY(calc(-1*(100% + 10px))) rotate3d(0,1,0,180deg);
        scale: 1;
    }
}

@keyframes moveCardMobile {
    20% {
        transform: translateX(-20%);
    }
    30% {
        transform: translateX(0) rotate3d(0,1,0,180deg) ;
        scale: 1;
    }
    50% {
        scale: 1.3;
    }
    100% {
        transform: translateY(calc(-1*(100% + 10px))) rotate3d(0,1,0,180deg);
        scale: 1.3;
    }
}

@media (max-width:600px) {
    .active {
        animation: moveCardMobile 5s;
        animation-fill-mode: forwards;
    }
}


</style>