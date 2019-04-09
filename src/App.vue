<template>
    <v-app dark>
        <v-layout row wrap>
            <v-flex xs3 flat class="sideBarWrap">
                <v-content>
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
                                            <v-btn class="mx-0" depressed light block @click="addText" disabled>Text
                                            </v-btn>
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
                                            <v-btn class="mx-0" depressed light block data-list="rotateList">Rotate
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pl-1">
                                            <v-btn class="mx-0" depressed light block data-list="shadowPopList">
                                                ShadowPop
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pr-1">
                                            <v-btn class="mx-0" depressed light block data-list="swirlInList">SwirlIn
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pl-1">
                                            <v-btn class="mx-0" depressed light block data-list="swirlOutList">
                                                SwirlOut
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pr-1">
                                            <v-btn class="mx-0" depressed light block data-list="bounceInList">
                                                BounceIn
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pl-1">
                                            <v-btn class="mx-0" depressed light block data-list="bounceOutList">
                                                BounceOut
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pr-1">
                                            <v-btn class="mx-0" depressed light block data-list="rollInList">RollIn
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pl-1">
                                            <v-btn class="mx-0" depressed light block data-list="rollOutList">RollOut
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pr-1">
                                            <v-btn class="mx-0" depressed light block data-list="fadeInList">FadeIn
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pl-1">
                                            <v-btn class="mx-0" depressed light block data-list="fadeOutList">FadeOut
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pr-1">
                                            <v-btn class="mx-0" depressed light block data-list="scaleUpList">ScaleUp
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pl-1">
                                            <v-btn class="mx-0" depressed light block data-list="scaleDownList">
                                                ScaleDown
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pr-1">
                                            <v-btn class="mx-0" depressed light block data-list="vibrate">Vibrate
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pl-1">
                                            <v-btn class="mx-0" depressed light block data-list="wobble">Wobble</v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pr-1">
                                            <v-btn class="mx-0" depressed light block data-list="pulsate">Pulsate
                                            </v-btn>
                                        </v-flex>
                                        <v-flex xs6 class="pl-1">
                                            <v-btn class="mx-0" depressed light block data-list="soaring">Soaring
                                            </v-btn>
                                        </v-flex>
                                    </v-layout>
                                    <v-layout row wrap class="my-2">
                                        <v-flex xs12 class="listContent" id="allSelectorsList">
                                            <form @change="optionEvent($event)">
                                                <div class="list rotateList">
                                                    <label for="rotate">Direction:</label>
                                                    <select class="form-control" id="rotate">
                                                        <option selected>None</option>
                                                        <option animation="rotate-left">Left</option>
                                                        <option animation="rotate-top">Top</option>
                                                        <option animation="rotate-right">Right</option>
                                                        <option animation="rotate-bottom">Bottom</option>
                                                        <option animation="rotate-center">Center</option>
                                                        <option animation="rotate-bl">Bottom-Left</option>
                                                        <option animation="rotate-br">Bottom-Right</option>
                                                        <option animation="rotate-tr">Top-Right</option>
                                                        <option animation="rotate-tl">Top-Left</option>
                                                    </select>
                                                </div>
                                                <div class="list shadowPopList">
                                                    <label for="shadowPop">Direction:</label>
                                                    <select class="form-control" id="shadowPop">
                                                        <option selected>None</option>
                                                        <option animation="shadow-pop-bl">Bottom-Left</option>
                                                        <option animation="shadow-pop-br">Bottom-Right</option>
                                                        <option animation="shadow-pop-tr">Top-Right</option>
                                                        <option animation="shadow-pop-tl">Top-Left</option>
                                                    </select>
                                                </div>
                                                <div class="list swirlInList">
                                                    <label for="swirlIn">Direction:</label>
                                                    <select class="form-control" id="swirlIn">
                                                        <option selected>None</option>
                                                        <option animation="swirl-in-fwd">Center</option>
                                                        <option animation="swirl-in-left-fwd">Left</option>
                                                        <option animation="swirl-in-top-fwd">Top</option>
                                                        <option animation="swirl-in-right-fwd">Right</option>
                                                        <option animation="swirl-in-bottom-fwd">Bottom</option>
                                                        <option animation="swirl-in-bl-fwd">Bottom-Left</option>
                                                        <option animation="swirl-in-br-fwd">Bottom-Right</option>
                                                        <option animation="swirl-in-tr-fwd">Top-Right</option>
                                                        <option animation="swirl-in-tl-fwd">Top-Left</option>
                                                    </select>
                                                </div>
                                                <div class="list swirlOutList">
                                                    <label for="swirlOut">Direction:</label>
                                                    <select class="form-control" id="swirlOut">
                                                        <option selected>None</option>
                                                        <option animation="swirl-out-bck">Center</option>
                                                        <option animation="swirl-out-left-bck">Left</option>
                                                        <option animation="swirl-out-top-bck">Top</option>
                                                        <option animation="swirl-out-right-bck">Right</option>
                                                        <option animation="swirl-out-bottom-bck">Bottom</option>
                                                        <option animation="swirl-out-bl-bck">Bottom-Left</option>
                                                        <option animation="swirl-out-br-bck">Bottom-Right</option>
                                                        <option animation="swirl-out-tr-bck">Top-Right</option>
                                                        <option animation="swirl-out-tl-bck">Top-Left</option>
                                                    </select>
                                                </div>
                                                <div class="list bounceInList">
                                                    <label for="bounceIn">Direction:</label>
                                                    <select class="form-control" id="bounceIn">
                                                        <option selected>None</option>
                                                        <option animation="bounce-in-bck">Center (scaleOut)</option>
                                                        <option animation="bounce-in-fwd">Center (scaleIn)</option>
                                                        <option animation="bounce-in-right">Right</option>
                                                        <option animation="bounce-in-bottom">Bottom</option>
                                                        <option animation="bounce-in-left">Left</option>
                                                        <option animation="bounce-in-top">Top</option>
                                                    </select>
                                                </div>
                                                <div class="list bounceOutList">
                                                    <label for="bounceOut">Direction:</label>
                                                    <select class="form-control" id="bounceOut">
                                                        <option selected>None</option>
                                                        <option animation="bounce-out-right">Right</option>
                                                        <option animation="bounce-out-bottom">Bottom</option>
                                                        <option animation="bounce-out-left">Left</option>
                                                        <option animation="bounce-out-top">Top</option>
                                                    </select>
                                                </div>
                                                <div class="list rollInList">
                                                    <label for="rollIn">Direction:</label>
                                                    <select class="form-control" id="rollIn">
                                                        <option selected>None</option>
                                                        <option animation="roll-in-right">Right</option>
                                                        <option animation="roll-in-bottom">Bottom</option>
                                                        <option animation="roll-in-left">Left</option>
                                                        <option animation="roll-in-top">Top</option>
                                                    </select>
                                                </div>
                                                <div class="list rollOutList">
                                                    <label for="rollOut">Direction:</label>
                                                    <select class="form-control" id="rollOut">
                                                        <option selected>None</option>
                                                        <option animation="roll-out-right">Right</option>
                                                        <option animation="roll-out-bottom">Bottom</option>
                                                        <option animation="roll-out-left">Left</option>
                                                        <option animation="roll-out-top">Top</option>
                                                    </select>
                                                </div>
                                                <div class="list fadeInList">
                                                    <label for="fadeIn">Direction:</label>
                                                    <select class="form-control" id="fadeIn">
                                                        <option selected>None</option>
                                                        <option animation="fade-in-left">Left</option>
                                                        <option animation="fade-in-top">Top</option>
                                                        <option animation="fade-in-right">Right</option>
                                                        <option animation="fade-in-bottom">Bottom</option>
                                                        <option animation="fade-in-fwd">Center</option>
                                                        <option animation="fade-in-bl">Bottom-Left</option>
                                                        <option animation="fade-in-br">Bottom-Right</option>
                                                        <option animation="fade-in-tr">Top-Right</option>
                                                        <option animation="fade-in-tl">Top-Left</option>
                                                    </select>
                                                </div>
                                                <div class="list fadeOutList">
                                                    <label for="fadeOut">Direction:</label>
                                                    <select class="form-control" id="fadeOut">
                                                        <option selected>None</option>
                                                        <option animation="fade-out-left">Left</option>
                                                        <option animation="fade-out-top">Top</option>
                                                        <option animation="fade-out-right">Right</option>
                                                        <option animation="fade-out-bottom">Bottom</option>
                                                        <option animation="fade-out-fwd">Center</option>
                                                        <option animation="fade-out-bl">Bottom-Left</option>
                                                        <option animation="fade-out-br">Bottom-Right</option>
                                                        <option animation="fade-out-tr">Top-Right</option>
                                                        <option animation="fade-out-tl">Top-Left</option>
                                                    </select>
                                                </div>
                                                <div class="list scaleUpList">
                                                    <label for="scaleUp">Direction:</label>
                                                    <select class="form-control" id="scaleUp">
                                                        <option selected>None</option>
                                                        <option animation="scale-up-left">Left</option>
                                                        <option animation="scale-up-top">Top</option>
                                                        <option animation="scale-up-right">Right</option>
                                                        <option animation="scale-up-bottom">Bottom</option>
                                                        <option animation="scale-up-center">Center</option>
                                                        <option animation="scale-up-bl">Bottom-Left</option>
                                                        <option animation="scale-up-br">Bottom-Right</option>
                                                        <option animation="scale-up-tr">Top-Right</option>
                                                        <option animation="scale-up-tl">Top-Left</option>
                                                    </select>
                                                </div>
                                                <div class="list scaleDownList">
                                                    <label for="scaleDown">Direction:</label>
                                                    <select class="form-control" id="scaleDown">
                                                        <option selected>None</option>
                                                        <option animation="scale-down-left">Left</option>
                                                        <option animation="scale-down-top">Top</option>
                                                        <option animation="scale-down-right">Right</option>
                                                        <option animation="scale-down-bottom">Bottom</option>
                                                        <option animation="scale-down-center">Center</option>
                                                        <option animation="scale-down-bl">Bottom-Left</option>
                                                        <option animation="scale-down-br">Bottom-Right</option>
                                                        <option animation="scale-down-tr">Top-Right</option>
                                                        <option animation="scale-down-tl">Top-Left</option>
                                                    </select>
                                                </div>
                                                <div class="list vibrate">
                                                    <label for="vibrate">Preset:</label>
                                                    <select class="form-control" id="vibrate">
                                                        <option selected>None</option>
                                                        <option animation="vibrate-1">Preset №1</option>
                                                        <option animation="vibrate-2">Preset №2</option>
                                                        <option animation="vibrate-3">Preset №3</option>
                                                    </select>
                                                </div>
                                                <div class="list wobble">
                                                    <label for="wobble">Preset:</label>
                                                    <select class="form-control" id="wobble">
                                                        <option selected>None</option>
                                                        <option animation="wobble-hor-top">Top</option>
                                                        <option animation="wobble-hor-bottom">Bottom</option>
                                                        <option animation="wobble-ver-left">Left</option>
                                                        <option animation="wobble-ver-right">Right</option>
                                                    </select>
                                                </div>
                                                <div class="list pulsate">
                                                    <label for="pulsate">Preset:</label>
                                                    <select class="form-control" id="pulsate">
                                                        <option selected>None</option>
                                                        <option animation="heartbeat">Heart beat</option>
                                                        <option animation="ping">Ping</option>
                                                        <option animation="pulsate-bck">Forwards</option>
                                                        <option animation="pulsate-fwd">Backwards</option>
                                                    </select>
                                                </div>
                                                <div class="list soaring">
                                                    <label for="soaring">Preset:</label>
                                                    <select class="form-control" id="soaring">
                                                        <option selected>None</option>
                                                        <option animation="float-hor">Vertical</option>
                                                        <option animation="float-ver">Horizontal</option>
                                                    </select>
                                                </div>
                                                <div class="list trackingInList">
                                                    <label for="trackingIn">Direction:</label>
                                                    <select class="form-control" id="trackingIn">
                                                        <option selected>None</option>
                                                        <option animation="tracking-in-expand-fwd-top">From top
                                                        </option>
                                                        <option animation="tracking-in-expand-fwd-bottom">From
                                                            bottom
                                                        </option>
                                                        <option animation="tracking-in-expand-fwd">Backwards
                                                        </option>
                                                        <option animation="tracking-in-contract-bck-bottom">To Top
                                                        </option>
                                                        <option animation="tracking-in-contract-bck-top">To Bottom
                                                        </option>
                                                        <option animation="tracking-in-contract-bck">Forwards
                                                        </option>
                                                    </select>
                                                </div>
                                                <div class="list trackingOutList">
                                                    <label for="trackingOut">Direction:</label>
                                                    <select class="form-control" id="trackingOut">
                                                        <option selected>None</option>
                                                        <option animation="tracking-out-expand-fwd-top">Top(width)
                                                        </option>
                                                        <option animation="tracking-out-expand-fwd-bottom">
                                                            Bottom(width)
                                                        </option>
                                                        <option animation="tracking-out-expand-fwd">Backwards
                                                        </option>
                                                        <option animation="tracking-out-contract-bck-bottom">Вверх
                                                        </option>
                                                        <option animation="tracking-out-contract-bck-top">Вниз
                                                        </option>
                                                        <option animation="tracking-out-contract-bck">Forwards
                                                        </option>
                                                    </select>
                                                </div>
                                                <div class="list focusIn">
                                                    <label for="focusIn">Direction:</label>
                                                    <select class="form-control" id="focusIn">
                                                        <option selected>None</option>
                                                        <option animation="text-focus-in">Center</option>
                                                        <option animation="focus-in-contract-bck">Forward</option>
                                                        <option animation="focus-in-expand-fwd">Backward</option>
                                                    </select>
                                                </div>
                                                <div class="list focusOut">
                                                    <label for="focusOut">Direction:</label>
                                                    <select class="form-control" id="focusOut">
                                                        <option selected>None</option>
                                                        <option animation="text-blur-out">Center</option>
                                                        <option animation="blur-out-contract-bck">Forward</option>
                                                        <option animation="blur-out-expand-fwd">Backward</option>
                                                    </select>
                                                </div>
                                                <div class="list flickerIn">
                                                    <label for="flickerIn">Direction:</label>
                                                    <select class="form-control" id="flickerIn">
                                                        <option selected>None</option>
                                                        <option animation="text-flicker-in-glow">Center</option>
                                                    </select>
                                                </div>
                                                <div class="list flickerOut">
                                                    <label for="flickerOut">Direction:</label>
                                                    <select class="form-control" id="flickerOut">
                                                        <option selected>None</option>
                                                        <option animation="text-flicker-out-glow">Center</option>
                                                    </select>
                                                </div>
                                                <div class="animationSettings">
                                                    <div class="inputWrap">
                                                        <label for="duration">Animation time (seconds):</label>
                                                        <input type="number" id="duration" class="form-control"
                                                               v-model="animationDuration"
                                                               value="1">
                                                    </div>
                                                    <div class="inputWrap">
                                                        <label for="function">Timing function:</label>
                                                        <select class="form-control" id="function"
                                                                v-model="animationFunction">
                                                            <option value="linear">Linear</option>
                                                            <option value="ease">Ease</option>
                                                            <option value="ease-in">EaseIn</option>
                                                            <option value="ease-out">EaseOut</option>
                                                            <option value="ease-in-out" selected>EaseInOut</option>
                                                        </select>
                                                    </div>
                                                    <div class="inputWrap">
                                                        <label for="delay">Delay (seconds):</label>
                                                        <input type="number" id="delay" class="form-control"
                                                               v-model="animationDelay"
                                                               value="0">
                                                    </div>
                                                    <div class="inputWrap">
                                                        <label for="iteration">Iteration count:</label>
                                                        <input type="number" id="iteration" class="form-control"
                                                               v-model="animationIteration"
                                                               value="1">
                                                        <label class="checkbox-inline">
                                                            <input type="checkbox"
                                                                   id="durationInf"
                                                                   value="infinite"
                                                                   @change="animationIteration = 'infinite'">
                                                            Infinite
                                                        </label>
                                                    </div>
                                                    <div class="inputWrap">
                                                        <label for="direction">Direction:</label>
                                                        <select class="form-control" id="direction"
                                                                v-model="animationDirection">
                                                            <option value="normal" selected>Normal</option>
                                                            <option value="alternate">Alternate</option>
                                                            <option value="reverse">Reverse</option>
                                                            <option value="alternate-reverse">Alternate-Reverse
                                                            </option>
                                                        </select>
                                                    </div>
                                                    <div class="inputWrap">
                                                        <label for="filling">Fill-mode:</label>
                                                        <select class="form-control" id="filling"
                                                                v-model="animationFilling">
                                                            <option value="none">None</option>
                                                            <option value="forwards">Forwards</option>
                                                            <option value="backwards">Backwards</option>
                                                            <option value="both" selected>Both</option>
                                                        </select>
                                                    </div>
                                                </div>
                                            </form>
                                        </v-flex>
                                    </v-layout>
                                </v-card-text>
                            </v-card>
                        </v-expansion-panel-content>
                    </v-expansion-panel>
                </v-content>
            </v-flex>
            <v-flex xs9>
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
            </v-flex>
        </v-layout>
    </v-app>
</template>

<script>
    export default {
        data() {
            return {
                items: [],
                panel: [true, false],
                disabled: true,
                disabledFirst: false,
                animationName: '',
                animationDelay: '0',
                animationDuration: '1',
                animationDirection: 'normal',
                animationFilling: 'both',
                animationIteration: '1',
                animationFunction: 'ease'
            }
        },
        methods: {
            addBlock() {
                this.clearArray();
                this.items.push({itemClass: 'blockExample', itemText: ''});
            },
            addText() {
                this.clearArray();
                this.items.push({itemClass: 'textExample', itemText: 'Text example'});
            },
            clearArray() {
                while (this.items.length > 0) {
                    this.items.pop();
                }

                this.disabled = false;
                this.disabledFirst = true;
                this.panel = [false, true];
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
            },
            optionEvent(obj) {
                let anObject = document.getElementsByClassName('blockExample')[0];
                document.getElementsByClassName('animationSettings')[0].style.display = 'block';

                anObject.style.animation = 'none';

                if (obj.target.parentElement.classList.contains('list')) {
                    this.animationName = obj.target.options[obj.target.options.selectedIndex].attributes.animation.value;
                }

                this.setAnimation();
            },
            setAnimation() {
                let objAnimation;
                let anObject = document.getElementsByClassName('blockExample')[0];
                anObject.style.animation = 'none';
                objAnimation = this.animationName + ' ' + this.animationDuration + 's ' + this.animationFunction + ' ' + this.animationDelay + 's ' + this.animationIteration + ' ' + this.animationDirection + ' ' + this.animationFilling;
                setTimeout(function () {
                    anObject.style.animation = objAnimation;
                }, 100);
            },
            replayAnimation() {
                this.setAnimation();
            }
        }
    }
</script>

<style>
    .sideBarWrap {
        background: #222;
    }

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

    .animationSettings {
        display: none;
    }

    select, input {
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
        transition: border-color .15s ease-in-out, box-shadow .15s ease-in-out;
    }

    input[type=number] {
        width: 100%;
    }

    input[type=checkbox] {
        display: inline;
        width: auto;
        margin-right: 10px;
    }

    .workAreaWrap {
        max-height: 100vh;
        min-height: calc(100vh - 48px);
    }

    .sideBarWrap {
        max-height: 100vh;
        overflow: auto;
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
