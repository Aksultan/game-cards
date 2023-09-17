<script lang="ts" setup>
defineProps<{
    suit: string,
    cardValue: string
}>()

const suitAlias: {[index: string]: string} = {
    'spade': '♠️',
    'diamond': '♦️',
    'heart': '♥️',
    'club': '♣️'
};
</script>
<template>
    <div :class="['card']">
        <div class="card-inner">
            <div class="card-front">
                <div :class="[`value${suit ? '__' + suit : ''}`, 'value']">
                    {{cardValue}}
                </div>
                <div class="suit">
                    {{ suitAlias[suit] }}
                </div>
            </div>
            <div class="card-back">
            </div>
        </div>
    </div>
</template>

<style>
.card-inner {
    position: relative;
    background-color: #fff;
    height: 20rem;
    width: 12rem;
    border-radius: 20px;
    transform-style: preserve-3d;
}

.card-front {
    display: flex;
    flex-direction: column;
    border-radius: 20px;
    padding: 10px 20px;
    transform: rotateY(180deg);
}

.card-back {
    background-color: #fff;
    border-radius: 20px;
    border: 2px solid #000;
}

.card-front, .card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden; /* Safari */
    backface-visibility: hidden;
}

.value {
    font-family: 'Rubik';
    font-size: 3rem;
    font-weight: 800;
    padding-left: 5px;
}

.suit {
    font-size: 2rem;
}

.value__spade, .value__club {
    color: #9b94ba;
}

.value__heart, .value__diamond {
    color: #fa7b7a;
}
</style>