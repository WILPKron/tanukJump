<template>
    <div class="pop-up__item_personage">
        <h2 class="pop-up__h">Выбери персонажа</h2>
        <div class="pop-up__personage-wrap">
            <button
                class="pop-up__personage"
                value="personage1"
                @click="choosePersonage"
                :style="{
                    backgroundPositionX:
                        selectedPersonage === 'personage1' ? '-240px' : '',
                }"
            ></button>
            <button
                class="pop-up__personage"
                value="personage2"
                @click="choosePersonage"
                :style="{
                    backgroundImage:
                        'url(' + require('../sprite/character2.png') + ')',
                    backgroundPositionX:
                        selectedPersonage === 'personage2' ? '-240px' : '',
                }"
            ></button>
            <button
                class="pop-up__personage"
                value="personage3"
                @click="choosePersonage"
                :style="{
                    backgroundImage:
                        'url(' + require('../sprite/character3.png') + ')',
                    backgroundPositionX:
                        selectedPersonage === 'personage3' ? '-240px' : '',
                }"
            ></button>
        </div>
        <div @click="next" class="pop-up__button-wrap">
            <button-g name="Выбрать"></button-g>
        </div>
    </div>
</template>
<script>
import buttonG from "../ui/button.vue";

export default {
    components: {
        buttonG,
    },
    data() {
        return {
            selectedPersonage: "personage1",
        };
    },
    methods: {
        next() {
            this.$store.commit("nextStape", "message");
        },
        choosePersonage(event) {
            this.selectedPersonage = event.currentTarget.value;
        },
    },
};
</script>
<style lang="scss">
.pop-up__item_personage {
    width: 100%;
}

.pop-up__h {
    font-weight: bold;
    font-size: 34px;
    line-height: 100%;
    text-transform: uppercase;
    color: #ffffff;
    text-align: center;
    margin: 0 0 50px;
}

.pop-up__personage-wrap {
    display: grid;
    grid-auto-flow: column;
    justify-content: space-around;
    grid-gap: 10px;
    width: 100%;
}

.pop-up__personage {
    width: 240px;
    height: 236px;
    display: block;
    padding: 0;
    margin: 0;
    border: 0;
    background-color: transparent;
    background-image: url("../sprite/character1.png");
    background-size: 480px;
    background-repeat: no-repeat;
    cursor: pointer;
}

.pop-up__button-wrap {
    margin-top: 36px;
    display: grid;
    grid-auto-flow: column;
    justify-content: center;
    grid-gap: 20px;
}
</style>
