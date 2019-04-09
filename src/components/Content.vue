<template>
    <v-container>
        <v-content>
            <div class="workAreaWrap">
                <div v-for="item in items" :class="item.itemClass">{{ item.itemText }}</div>
                <v-btn dark fab @click="replayAnimation()" class="replayButton">
                    <i class="material-icons">
                        autorenew
                    </i>
                </v-btn>
            </div>
        </v-content>
    </v-container>
</template>

<script>
    import {eventBus} from "@/main";

    export default {
        name: "Home",
        data() {
            return {
                items: []
            }
        },
        methods: {
            replayAnimation() {
                eventBus.$emit('replayAnimation');
            }
        },
        created() {
            eventBus.$on('objectWasChosen', (array) => {
                this.items = array;
            });
        }
    }
</script>

<style>
    .workAreaWrap {
        max-height: 100vh;
        min-height: calc(100vh - 48px);
    }

    .blockExample {
        position: absolute;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        margin: auto;

        background: #fff;
        width: 100px;
        height: 100px;
    }

    .replayButton {
        position: fixed !important;
        top: 20px;
        right: 20px;
    }
</style>