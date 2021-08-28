<template>
    
    <div @click="countUp" @click.right="countUp">
        <div id="content">
            <h1>POPME</h1>
            <p>{{ counter }}</p>
        </div>

        <div class="main">
            <img src="https://i.pinimg.com/originals/cd/55/04/cd55044d19292355fbe2e254105e75af.jpg" alt="">
        </div>

        <div id="images">
            <img class="bg" src="https://c.tenor.com/EcPMs2vaS9kAAAAC/in-hell.gif" alt="">
        </div>
    </div>
</template>

<script setup>

    import { ref } from 'vue'
    import { Howl } from 'howler'

    const counter = ref(0);

    const quack = new Howl({
        src: ['./audio.mp3']
    });

    const countUp = () => {
        
        if (quack.playing([0])) {
            quack.stop()
        }

        counter.value++;
        quack.play();
    }

</script>

<style scoped>
    #content {
        position: absolute;
        z-index: 3;
        text-align: center;
        width: 100%;
        margin-top: 10px;
        font-family: 'Titan One', cursive;
        color: black;
        -webkit-text-fill-color: white;
        -webkit-text-stroke-width: 3px;
        -webkit-text-stroke-color: black;
    }

    #content h1 {
        margin: 0;
        font-size: 90px;
    }

    #content p {
        margin: 0;
        font-size: 60px;
    }

    .main img {
        position: absolute;
        z-index: 2;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
    }
    
    #images .bg {
        position: relative;
        z-index: 1;
        width: 100%;
        height: 100%;
        object-fit: cover;
        box-sizing: border-box;
    }
</style>