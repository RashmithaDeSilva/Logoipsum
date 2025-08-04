<script setup>
import twitter from '../assets/Icons/Twitter White.svg';
import youtube from '../assets/Icons/Youtube White.svg';

</script>


<template>
    <footer>
        <div class="footer-box">
            <div>
                <h1>Amadeus IT Group</h1>
                <p>C. Salvador de Madariaga, 1</p>
                <p>28027 Madrid</p>
                <p>Spain</p>
            </div>
            <div class="box-top-right">
                <p>Follow us on</p>
                <a href="#">
                    <img :src="twitter" alt="Icon"></img>
                </a>
                <a href="#">
                    <img :src="youtube" alt="Icon"></img>
                </a>
            </div>
        </div>

        <hr />

        <div class="footer-box box-bottom">
            <div>
                <p>Copyright © 2022 Amadeus Hotels. All rights reserved.</p>
            </div>
            <div>
                <p>Photos by Felix Mooneeram & Serge Kutuzov on Unsplash</p>
            </div>
        </div>
    </footer>
</template>


<style scoped>
footer {
    height: 16rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 2rem;
    background-color: rgb(48, 45, 45);
    color: white;
}
.footer-box {
    padding: 0rem 10rem;
    display: flex;
    justify-content: space-between;
    flex-direction: row; 
}
.box-bottom {
    color: grey;
}
.box-top-right {
    display: flex;
    gap: 1rem;
}
@media (max-width: 640px) {
    footer {
        height: 20rem;
    }
    .footer-box {
        flex-direction: column;
        gap: 1rem;
        padding: 0 2rem;
        text-align: center;
        align-items: center;
    }
}
@media (min-width: 641px) and (max-width: 1023px) {
    footer {
        height: 20rem;
    }
    .box-bottom {
        flex-direction: row;
        flex-wrap: wrap;
        padding: 0 2rem;
        gap: 1rem;
        text-align: center;
        justify-content: center;
    }
    .box-top {
        gap: 3rem;
    }
}
</style>
