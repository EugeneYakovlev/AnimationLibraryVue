<template>
    <div class="workAreaWrap">
        <div v-for="item in items" :class="item.itemClass">{{ item.itemText }}</div>
    </div>
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
        created() {
            eventBus.$on('objectWasChosen', (array) => {
                this.items = array;
            });
        }
    }
</script>

<style scoped>
    .blockExample {
        background: #fff;
        width: 50px;
        height: 50px;
    }
</style>