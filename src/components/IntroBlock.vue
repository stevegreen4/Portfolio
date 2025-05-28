<script setup>
import profilePicture from '../assets/profile-picture.png'
</script>

<template>
    <div class="intro-container">
        <img :src="profilePicture" alt="Good picture of myself">
        <p>
            Hello, and welcome to my site. Everything you see here was crafted by me using my skills as a 
            software developer. Please click around and learn more about all of my skills and expertise. 
            Once your done, reach out to me on linkedIn and we can talk about how I will be a great asset to your team.
        </p>
    </div>
    
</template>

<style scoped>
.intro-container {
    margin-top: 100px;
    display: flex;
    align-items: center;
    gap: 2rem;
}

.intro-container img {
    width: 150px;
    height: 150px;
    object-fit: cover;
    border-radius: 50%;  
    border: 2px solid #e0e0e0;  
}

.intro-container p {
    line-height: 1.6;
}
</style>