<template>
    <ion-header class="main-background">
        <ion-toolbar>
            <ion-buttons slot="start">
                <ion-back-button id="search-button"></ion-back-button>
            </ion-buttons>
            <ion-title id="header"><em>WebStart Weather</em></ion-title>
        </ion-toolbar>
    </ion-header>
</template>

<script>
    export default {
        name: 'Header',
    }
</script>

<style lang="scss">
    #search-button {
        background: #101f3e;
        color: #101f3e;
    }
    #header {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        text-align: center;
        color: #8bc6ff;
        background: #101f3e;
        font-size: 1.5rem;
        width: 100%;
        padding: 0;
    }
    .main-background {
        background: #101f3e;
    }
    .main-color {
        color: #8bc6ff;
    }
</style>