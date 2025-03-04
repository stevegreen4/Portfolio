<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
    <header>
        <h2><RouterLink to="/">Stephen Green</RouterLink></h2>
        <ul class="nav-block">
            <li><a href='../../public/Stephen Green Resume.pdf' target="_blank">Resume</a></li>
            <li><a href="https://www.linkedin.com/in/stevedgreen/" target="_blank">LinkedIn</a></li>
            <li><a href="https://github.com/stevegreen4" target="_blank">GitHub</a></li>
            <li><RouterLink to="/about">About</RouterLink></li>
        </ul>
    </header>
</template>

<style scoped>
header {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 80px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    background-color: rgba(0, 0, 0, 0.8);
    z-index: 1000;
}

header h2 {
    margin: 0;
    font-size: 3rem;
}

header h2 a,
header h2 RouterLink {
    text-decoration: none;
    color: white;
}

.nav-block {
    display: flex;
    align-items: center;
    margin: 0;
    padding: 30px;
}

.nav-block li {
    list-style: none;
    padding: 0 15px;
}

.nav-block li a,
.nav-block li RouterLink {
    text-decoration: none;
    color: white;
    font-size: 1.1rem;
    transition: color 0.3s ease;
}

.nav-block li a:hover,
.nav-block li RouterLink:hover {
    color: #ccc;
}
</style>