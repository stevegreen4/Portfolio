<script setup>

</script>

<template>
    <ul>
        <li>
            bullet point for skill 
        </li>
        <li>
            bullet point 
        </li>
    </ul>
    <div class="pic-container">
        <img src="../assets/RMSG-Transparent.png" alt="Rocky Mountain State Games">
        <img src="../assets/reindeer-run.png" alt="reindeer run">  
        <img src="../assets/csldlo.png" alt="Labor Day Liftoff">  
    </div>
   
</template>

<style scoped>
.pic-container {
    display: flex;
    justify-content: center;
    gap: 2rem;
    margin: 2rem 0;
}

.pic-container img {
    width: 300px;  /* Fixed width */
    height: 200px; /* Fixed height */
    object-fit: contain; /* Maintains aspect ratio */
    padding: 1rem;
    border-radius: 8px;
}

/* Responsive design */
@media (max-width: 768px) {
    .pic-container {
        flex-direction: column;
        align-items: center;
    }

    .pic-container img {
        width: 100%;
        max-width: 300px;
    }
}
</style>