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

.card {
    width: 12em;
    height: 20em;
}

.card-inner, .card-front, .card-back {
    border-radius: var(--border-radius-m);
}

.card-inner {
    position: relative;
    background-color: var(--secondary-color);
    transform-style: preserve-3d;
}

.card-front {
    display: flex;
    flex-direction: column;
    padding: var(--padding);
    transform: rotateY(180deg);
}

.card-back {
    background: var(--gradient); 
    border: 2px solid var(--main-color);
}

.card-inner, .card-front, .card-back {
    width: 100%;
    height: 100%;
}

.card-front, .card-back {
    position: absolute;
    -webkit-backface-visibility: hidden;
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
    color: var(--card-suit-black);
}

.value__heart, .value__diamond {
    color: var(--card-suit-red);
}

@media (max-width:600px) {
    .card {
        width: 10em;
        height: 15em;
    }

    .card-front, .card-back, .card-inner {
        border-radius: var(--border-radius-s);
    }
}

@media (max-width: 500px) {
    .card {
        width: 8em;
        height: 12em;
    }
}

@media (max-width: 400px) {
    .card {
        width: 6em;
        height: 9em;
    }

    .value {
        font-size: 2rem;
        padding: 0;
    }

    .suit {
        font-size: 1rem;
    }
}


</style>