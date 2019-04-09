<template>
    <v-app dark>
        <v-layout row wrap>
            <v-flex xs3 flat class="sideBarWrap">
                <app-sidebar></app-sidebar>
            </v-flex>
            <v-flex xs9>
                <app-content></app-content>
            </v-flex>
        </v-layout>
    </v-app>
</template>

<script>
    import Sidebar from './components/Sidebar.vue';
    import Content from './components/Content.vue';

    export default {
        components: {
            appSidebar: Sidebar,
            appContent: Content
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

    .sideBarWrap {
        max-height: 100vh;
        overflow: auto;
    }
</style>
