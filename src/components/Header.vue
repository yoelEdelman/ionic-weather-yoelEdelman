<template>
    <ion-header>
        <ion-toolbar>
            <ion-buttons slot="start">
                <ion-back-button></ion-back-button>
            </ion-buttons>
            <ion-title id="header"><em>OpenWeather</em></ion-title>
        </ion-toolbar>
    </ion-header>
</template>

<script>
    export default {
        name: 'Header',
    }
</script>

<style lang="scss">
    #header {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        text-align: center;
        color: aqua;
        background: black;
        font-size: 1.5rem;
    }
</style>