<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected: selected && !open }">
            <Gift v-if="open && hasGift" />
        </div>
        <div class="door" :class="{ open }"
            @click="selected = !selected">
            <div class="number" :class="{ selected }">{{ number }}</div>
            <div class="knob" :class="{ selected }"
                @click.stop="open = true"></div>
        </div>
    </div>
</template>

<script>
import Gift from './Gift'

export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Door',
    components: { Gift },
    props: {
        number: {},
        hasGift: { type: Boolean }
    },
    data: function() {
        return {
            open: false,
            selected: false
        }
    }
}
</script>

<style>
:root {
    --door-border: 5px solid #82A6B1;
    --selected-border: 5px solid #DDE5B6;
}

.door-area {
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 20px solid #AAA;
    margin-bottom: 20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;
}

.door-frame {
    position: absolute;
    height: 300px;
    width: 180px;

    border-left: var(--door-border);
    border-top: var(--door-border);
    border-right: var(--door-border);

    display: flex;
    justify-content: center;
    align-items: flex-end;
}

.door {
    position: absolute;
    top: 5px;
    height: 295px;
    width: 170px;
    background-color: #143642;

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 15px;
}

.door .knob {
    height: 20px;
    width: 20px;
    border-radius: 10px;
    background-color: #82A6B1;
    align-self: flex-start;
    margin-top: 60px;
}

.door-frame.selected {
    border-left: var(--selected-border);
    border-top: var(--selected-border);
    border-right: var(--selected-border);
}

.door > .number.selected {
    color: #DDE5B6;
}

.door > .knob.selected {
    background-color: #DDE5B6;
}

.door.open {
    background-color: #0007;
}

.door.open .knob {
    display: none;
}

.door.open .number {
    display: none;
}
</style>