<template>
    <v-app dark>
        <v-layout row wrap>
            <v-flex xs3 flat class="sideBarWrap">
                <v-content>
                    <app-sidebar></app-sidebar>
                </v-content>
            </v-flex>
            <v-flex xs9>
                <v-container>
                    <v-content>
                        <app-main></app-main>
                    </v-content>
                </v-container>
            </v-flex>
        </v-layout>
    </v-app>
</template>

<script>
    import Sidebar from './components/Sidebar.vue';
    import Home from './components/Home.vue'

    export default {
        name: 'App',
        components: {
            appSidebar: Sidebar,
            appMain: Home
        },
        data() {
            return {
                //
            }
        }
    }
</script>

<style>
    .sideBarWrap {
        background: #222;
    }
</style>
