<script setup>
</script>
<template>
    <p class=" text-center">css测试</p>
    <div class="all">
        <div class="box">
            <a class="card" href>
                <i class="fa-brands fa-github"></i>
            </a>
            <a class="card" href>
                <i class="fa-brands fa-instagram"></i>
            </a>
            <a class="card" href>
                <i class="fa-brands fa-tiktok"></i>
            </a>
            <a class="card" href>
                <i class="fa-brands fa-youtube"></i>
            </a>
            <a class="card" href>
                <i class="fa-brands fa-twitter"></i>
            </a>
            <a class="card" href>
                <i class="fa-brands fa-facebook"></i>
            </a>
            <a class="card" href>
                <i class="fa-brands fa-twitch"></i>
            </a>
            <a class="card" href>
                <i class="fa-brands fa-steam"></i>
            </a>
            <a class="card" href>
                <i class="fa-brands fa-xbox"></i>
            </a>
            <div class="bg"></div>
        </div>
    </div>
</template>
<style scoped>
@import url('https://lf6-cdn-tos.bytecdntp.com/cdn/expire-1-M/font-awesome/6.0.0/css/all.min.css');

* {
    padding: 0;
    margin: 0;
    transition: all 0.5s;
}

.all {
    display: flex;
    justify-content: center;
    align-items: center;
}

.box {
    position: relative;
    display: grid;
    grid-template-columns: auto auto auto;
    gap: 0px;
}

.box:hover .bg {
    opacity: 0;
    transition: opacity 0.5s;
    z-index: -1;
}

.box:hover {
    gap: 2vw;
    transition: gap 0.6s;
}

.box:hover .card {
    border-radius: 2vh;
    box-shadow: 0px 0px 50px 5px rgba(0, 0, 0, 0.3);
    opacity: 1;
    transition: opacity 0.8s, border-radius 1s;

}

.card {
    background-color: rgb(187, 187, 187);
    font-size: 3rem;
    color: black;
    width: 10vw;
    aspect-ratio: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.8);
    opacity: 0;
    transition: background-color 0.5s;
}

.card:hover {
    background-color: rgb(208, 255, 218);
}

.bg {
    opacity: 1;
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 3rem;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    box-shadow: inset 0px 0px 200px #fff;
    background: linear-gradient(0deg, rgb(245, 201, 164), rgb(191, 236, 185), rgb(157, 210, 226));
}</style>