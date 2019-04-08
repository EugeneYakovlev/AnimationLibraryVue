<template>
    <div>
        <v-expansion-panel dark v-model="panel" expand="">
            <v-expansion-panel-content :disabled="disabledFirst">
                <template v-slot:header>
                    <div class="headline font-weight-thin">Chose animation object</div>
                </template>
                <v-card>
                    <v-card-text class="py-0">
                        <v-layout row wrap class="my-2">
                            <v-flex xs6 class="pr-1">
                                <v-btn class="mx-0" depressed light block @click="addBlock">Block</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pl-1">
                                <v-btn class="mx-0" depressed light block @click="addText" disabled>Text</v-btn>
                            </v-flex>
                        </v-layout>
                    </v-card-text>
                </v-card>
            </v-expansion-panel-content>
            <v-expansion-panel-content :disabled="disabled">
                <template v-slot:header>
                    <div class="headline font-weight-thin">Chose animation preset</div>
                </template>
                <v-card>
                    <v-card-text class="py-0">
                        <v-layout row wrap class="presetList my-2" @click="openDirection($event)">
                            <v-flex xs6 class="pr-1">
                                <v-btn class="mx-0" depressed light block data-list="rotateList">Rotate</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pl-1">
                                <v-btn class="mx-0" depressed light block data-list="shadowPopList">ShadowPop</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pr-1">
                                <v-btn class="mx-0" depressed light block data-list="swirlInList">SwirlIn</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pl-1">
                                <v-btn class="mx-0" depressed light block data-list="swirlOutList">SwirlOut</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pr-1">
                                <v-btn class="mx-0" depressed light block data-list="bounceInList">BounceIn</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pl-1">
                                <v-btn class="mx-0" depressed light block data-list="bounceOutList">BounceOut</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pr-1">
                                <v-btn class="mx-0" depressed light block data-list="rollInList">RollIn</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pl-1">
                                <v-btn class="mx-0" depressed light block data-list="rollOutList">RollOut</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pr-1">
                                <v-btn class="mx-0" depressed light block data-list="fadeInList">FadeIn</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pl-1">
                                <v-btn class="mx-0" depressed light block data-list="fadeOutList">FadeOut</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pr-1">
                                <v-btn class="mx-0" depressed light block data-list="scaleUpList">ScaleUp</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pl-1">
                                <v-btn class="mx-0" depressed light block data-list="scaleDownList">ScaleDown</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pr-1">
                                <v-btn class="mx-0" depressed light block data-list="vibrate">Vibrate</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pl-1">
                                <v-btn class="mx-0" depressed light block data-list="wobble">Wobble</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pr-1">
                                <v-btn class="mx-0" depressed light block data-list="pulsate">Pulsate</v-btn>
                            </v-flex>
                            <v-flex xs6 class="pl-1">
                                <v-btn class="mx-0" depressed light block data-list="soaring">Soaring</v-btn>
                            </v-flex>
                        </v-layout>
                        <v-layout row wrap class="my-2">
                            <v-flex xs12 class="listContent" id="allSelectorsList">
                                <div class="list rotateList">
                                    <label for="rotate">Direction:</label>
                                    <select class="form-control" id="rotate">
                                        <option selected>None</option>
                                        <option data-animation_name="rotate-left">Left</option>
                                        <option data-animation_name="rotate-top">Top</option>
                                        <option data-animation_name="rotate-right">Right</option>
                                        <option data-animation_name="rotate-bottom">Bottom</option>
                                        <option data-animation_name="rotate-center">Center</option>
                                        <option data-animation_name="rotate-bl">Bottom-Left</option>
                                        <option data-animation_name="rotate-br">Bottom-Right</option>
                                        <option data-animation_name="rotate-tr">Top-Right</option>
                                        <option data-animation_name="rotate-tl">Top-Left</option>
                                    </select>
                                </div>
                                <div class="list shadowPopList">
                                    <label for="shadowPop">Direction:</label>
                                    <select class="form-control" id="shadowPop">
                                        <option selected>None</option>
                                        <option data-animation_name="shadow-pop-bl">Bottom-Left</option>
                                        <option data-animation_name="shadow-pop-br">Bottom-Right</option>
                                        <option data-animation_name="shadow-pop-tr">Top-Right</option>
                                        <option data-animation_name="shadow-pop-tl">Top-Left</option>
                                    </select>
                                </div>
                                <div class="list swirlInList">
                                    <label for="swirlIn">Direction:</label>
                                    <select class="form-control" id="swirlIn">
                                        <option selected>None</option>
                                        <option data-animation_name="swirl-in-fwd">Center</option>
                                        <option data-animation_name="swirl-in-left-fwd">Left</option>
                                        <option data-animation_name="swirl-in-top-fwd">Top</option>
                                        <option data-animation_name="swirl-in-right-fwd">Right</option>
                                        <option data-animation_name="swirl-in-bottom-fwd">Bottom</option>
                                        <option data-animation_name="swirl-in-bl-fwd">Bottom-Left</option>
                                        <option data-animation_name="swirl-in-br-fwd">Bottom-Right</option>
                                        <option data-animation_name="swirl-in-tr-fwd">Top-Right</option>
                                        <option data-animation_name="swirl-in-tl-fwd">Top-Left</option>
                                    </select>
                                </div>
                                <div class="list swirlOutList">
                                    <label for="swirlOut">Direction:</label>
                                    <select class="form-control" id="swirlOut">
                                        <option selected>None</option>
                                        <option data-animation_name="swirl-out-bck">Center</option>
                                        <option data-animation_name="swirl-out-left-bck">Left</option>
                                        <option data-animation_name="swirl-out-top-bck">Top</option>
                                        <option data-animation_name="swirl-out-right-bck">Right</option>
                                        <option data-animation_name="swirl-out-bottom-bck">Bottom</option>
                                        <option data-animation_name="swirl-out-bl-bck">Bottom-Left</option>
                                        <option data-animation_name="swirl-out-br-bck">Bottom-Right</option>
                                        <option data-animation_name="swirl-out-tr-bck">Top-Right</option>
                                        <option data-animation_name="swirl-out-tl-bck">Top-Left</option>
                                    </select>
                                </div>
                                <div class="list bounceInList">
                                    <label for="bounceIn">Direction:</label>
                                    <select class="form-control" id="bounceIn">
                                        <option selected>None</option>
                                        <option data-animation_name="bounce-in-bck">Center (scaleOut)</option>
                                        <option data-animation_name="bounce-in-fwd">Center (scaleIn)</option>
                                        <option data-animation_name="bounce-in-right">Right</option>
                                        <option data-animation_name="bounce-in-bottom">Bottom</option>
                                        <option data-animation_name="bounce-in-left">Left</option>
                                        <option data-animation_name="bounce-in-top">Top</option>
                                    </select>
                                </div>
                                <div class="list bounceOutList">
                                    <label for="bounceOut">Direction:</label>
                                    <select class="form-control" id="bounceOut">
                                        <option selected>None</option>
                                        <option data-animation_name="bounce-out-right">Right</option>
                                        <option data-animation_name="bounce-out-bottom">Bottom</option>
                                        <option data-animation_name="bounce-out-left">Left</option>
                                        <option data-animation_name="bounce-out-top">Top</option>
                                    </select>
                                </div>
                                <div class="list rollInList">
                                    <label for="rollIn">Direction:</label>
                                    <select class="form-control" id="rollIn">
                                        <option selected>None</option>
                                        <option data-animation_name="roll-in-right">Right</option>
                                        <option data-animation_name="roll-in-bottom">Bottom</option>
                                        <option data-animation_name="roll-in-left">Left</option>
                                        <option data-animation_name="roll-in-top">Top</option>
                                    </select>
                                </div>
                                <div class="list rollOutList">
                                    <label for="rollOut">Direction:</label>
                                    <select class="form-control" id="rollOut">
                                        <option selected>None</option>
                                        <option data-animation_name="roll-out-right">Right</option>
                                        <option data-animation_name="roll-out-bottom">Bottom</option>
                                        <option data-animation_name="roll-out-left">Left</option>
                                        <option data-animation_name="roll-out-top">Top</option>
                                    </select>
                                </div>
                                <div class="list fadeInList">
                                    <label for="fadeIn">Direction:</label>
                                    <select class="form-control" id="fadeIn">
                                        <option selected>None</option>
                                        <option data-animation_name="fade-in-left">Left</option>
                                        <option data-animation_name="fade-in-top">Top</option>
                                        <option data-animation_name="fade-in-right">Right</option>
                                        <option data-animation_name="fade-in-bottom">Bottom</option>
                                        <option data-animation_name="fade-in-fwd">Center</option>
                                        <option data-animation_name="fade-in-bl">Bottom-Left</option>
                                        <option data-animation_name="fade-in-br">Bottom-Right</option>
                                        <option data-animation_name="fade-in-tr">Top-Right</option>
                                        <option data-animation_name="fade-in-tl">Top-Left</option>
                                    </select>
                                </div>
                                <div class="list fadeOutList">
                                    <label for="fadeOut">Direction:</label>
                                    <select class="form-control" id="fadeOut">
                                        <option selected>None</option>
                                        <option data-animation_name="fade-out-left">Left</option>
                                        <option data-animation_name="fade-out-top">Top</option>
                                        <option data-animation_name="fade-out-right">Right</option>
                                        <option data-animation_name="fade-out-bottom">Bottom</option>
                                        <option data-animation_name="fade-out-fwd">Center</option>
                                        <option data-animation_name="fade-out-bl">Bottom-Left</option>
                                        <option data-animation_name="fade-out-br">Bottom-Right</option>
                                        <option data-animation_name="fade-out-tr">Top-Right</option>
                                        <option data-animation_name="fade-out-tl">Top-Left</option>
                                    </select>
                                </div>
                                <div class="list scaleUpList">
                                    <label for="scaleUp">Direction:</label>
                                    <select class="form-control" id="scaleUp">
                                        <option selected>None</option>
                                        <option data-animation_name="scale-up-left">Left</option>
                                        <option data-animation_name="scale-up-top">Top</option>
                                        <option data-animation_name="scale-up-right">Right</option>
                                        <option data-animation_name="scale-up-bottom">Bottom</option>
                                        <option data-animation_name="scale-up-center">Center</option>
                                        <option data-animation_name="scale-up-bl">Bottom-Left</option>
                                        <option data-animation_name="scale-up-br">Bottom-Right</option>
                                        <option data-animation_name="scale-up-tr">Top-Right</option>
                                        <option data-animation_name="scale-up-tl">Top-Left</option>
                                    </select>
                                </div>
                                <div class="list scaleDownList">
                                    <label for="scaleDown">Direction:</label>
                                    <select class="form-control" id="scaleDown">
                                        <option selected>None</option>
                                        <option data-animation_name="scale-down-left">Left</option>
                                        <option data-animation_name="scale-down-top">Top</option>
                                        <option data-animation_name="scale-down-right">Right</option>
                                        <option data-animation_name="scale-down-bottom">Bottom</option>
                                        <option data-animation_name="scale-down-center">Center</option>
                                        <option data-animation_name="scale-down-bl">Bottom-Left</option>
                                        <option data-animation_name="scale-down-br">Bottom-Right</option>
                                        <option data-animation_name="scale-down-tr">Top-Right</option>
                                        <option data-animation_name="scale-down-tl">Top-Left</option>
                                    </select>
                                </div>
                                <div class="list vibrate">
                                    <label for="vibrate">Preset:</label>
                                    <select class="form-control" id="vibrate">
                                        <option selected>None</option>
                                        <option data-animation_name="vibrate-1">Preset №1</option>
                                        <option data-animation_name="vibrate-2">Preset №2</option>
                                        <option data-animation_name="vibrate-3">Preset №3</option>
                                    </select>
                                </div>
                                <div class="list wobble">
                                    <label for="wobble">Preset:</label>
                                    <select class="form-control" id="wobble">
                                        <option selected>None</option>
                                        <option data-animation_name="wobble-hor-top">Top</option>
                                        <option data-animation_name="wobble-hor-bottom">Bottom</option>
                                        <option data-animation_name="wobble-ver-left">Left</option>
                                        <option data-animation_name="wobble-ver-right">Right</option>
                                    </select>
                                </div>
                                <div class="list pulsate">
                                    <label for="pulsate">Preset:</label>
                                    <select class="form-control" id="pulsate">
                                        <option selected>None</option>
                                        <option data-animation_name="heartbeat">Heart beat</option>
                                        <option data-animation_name="ping">Ping</option>
                                        <option data-animation_name="pulsate-bck">Forwards</option>
                                        <option data-animation_name="pulsate-fwd">Backwards</option>
                                    </select>
                                </div>
                                <div class="list soaring">
                                    <label for="soaring">Preset:</label>
                                    <select class="form-control" id="soaring">
                                        <option selected>None</option>
                                        <option data-animation_name="float-hor">Vertical</option>
                                        <option data-animation_name="float-ver">Horizontal</option>
                                    </select>
                                </div>
                                <div class="list trackingInList">
                                    <label for="trackingIn">Direction:</label>
                                    <select class="form-control" id="trackingIn">
                                        <option selected>None</option>
                                        <option data-animation_name="tracking-in-expand-fwd-top">From top</option>
                                        <option data-animation_name="tracking-in-expand-fwd-bottom">From bottom</option>
                                        <option data-animation_name="tracking-in-expand-fwd">Backwards</option>
                                        <option data-animation_name="tracking-in-contract-bck-bottom">To Top</option>
                                        <option data-animation_name="tracking-in-contract-bck-top">To Bottom</option>
                                        <option data-animation_name="tracking-in-contract-bck">Forwards</option>
                                    </select>
                                </div>
                                <div class="list trackingOutList">
                                    <label for="trackingOut">Direction:</label>
                                    <select class="form-control" id="trackingOut">
                                        <option selected>None</option>
                                        <option data-animation_name="tracking-out-expand-fwd-top">Top(width)</option>
                                        <option data-animation_name="tracking-out-expand-fwd-bottom">Bottom(width)
                                        </option>
                                        <option data-animation_name="tracking-out-expand-fwd">Backwards</option>
                                        <option data-animation_name="tracking-out-contract-bck-bottom">Вверх</option>
                                        <option data-animation_name="tracking-out-contract-bck-top">Вниз</option>
                                        <option data-animation_name="tracking-out-contract-bck">Forwards</option>
                                    </select>
                                </div>
                                <div class="list focusIn">
                                    <label for="focusIn">Direction:</label>
                                    <select class="form-control" id="focusIn">
                                        <option selected>None</option>
                                        <option data-animation_name="text-focus-in">Center</option>
                                        <option data-animation_name="focus-in-contract-bck">Forward</option>
                                        <option data-animation_name="focus-in-expand-fwd">Backward</option>
                                    </select>
                                </div>
                                <div class="list focusOut">
                                    <label for="focusOut">Direction:</label>
                                    <select class="form-control" id="focusOut">
                                        <option selected>None</option>
                                        <option data-animation_name="text-blur-out">Center</option>
                                        <option data-animation_name="blur-out-contract-bck">Forward</option>
                                        <option data-animation_name="blur-out-expand-fwd">Backward</option>
                                    </select>
                                </div>
                                <div class="list flickerIn">
                                    <label for="flickerIn">Direction:</label>
                                    <select class="form-control" id="flickerIn">
                                        <option selected>None</option>
                                        <option data-animation_name="text-flicker-in-glow">Center</option>
                                    </select>
                                </div>
                                <div class="list flickerOut">
                                    <label for="flickerOut">Direction:</label>
                                    <select class="form-control" id="flickerOut">
                                        <option selected>None</option>
                                        <option data-animation_name="text-flicker-out-glow">Center</option>
                                    </select>
                                </div>
                            </v-flex>
                        </v-layout>
                    </v-card-text>
                </v-card>
            </v-expansion-panel-content>
        </v-expansion-panel>
    </div>
</template>

<script>
    import {eventBus} from "@/main";

    export default {
        data() {
            return {
                items: [],
                panel: [true, false],
                disabled: true,
                disabledFirst: false
            }
        },
        methods: {
            addBlock() {
                this.clearArray();
                this.items.push({itemClass: 'blockExample', itemText: ''});
                this.sendArray();
            },
            addText() {
                this.clearArray();
                this.items.push({itemClass: 'textExample', itemText: 'Text example'});
                eventBus.$emit('objectWasChosen', this.items);
            },
            clearArray() {
                while (this.items.length > 0) {
                    this.items.pop();
                }

                this.disabled = false;
                this.disabledFirst = true;
                this.panel = [false, true];
            },
            sendArray() {
                eventBus.$emit('objectWasChosen', this.items);
            },
            openDirection(event) {
                let className = event.target.getAttribute('data-list');
                this.resetSelected();
                document.getElementById('allSelectorsList').getElementsByClassName(className)[0].style.display = "block";
            },
            resetSelected() {
                let parentID = document.getElementById('allSelectorsList');
                let subs = parentID.getElementsByClassName('list');

                for (let i = 0; i < subs.length; i++) {
                    let a = subs[i];
                    a.style.display = 'none';
                }
            }
        },
        created() {

        }
    }
</script>

<style>
    .v-expansion-panel {
        box-shadow: none;
    }

    .theme--dark.v-expansion-panel .v-expansion-panel__container {
        background: #222;
    }

    .listContent .list {
        display: none;
    }

    .v-card .v-btn__content {
        pointer-events: none !important;
    }

    select {
        margin: 5px 0;
        display: block;
        width: 100%;
        padding: .375rem .75rem;
        font-size: 1rem;
        line-height: 1.5;
        color: #222 !important;
        background-color: #fff !important;
        background-clip: padding-box;
        border: 1px solid #ced4da;
        border-radius: 2px;
        transition: border-color .15s ease-in-out,box-shadow .15s ease-in-out;
    }
</style>