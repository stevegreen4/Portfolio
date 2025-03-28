<script setup>

</script>

<template>
    <h4>
        I have put on various events from local 5k's to international affairs hosting thousands of people. 
        Check out some of the skills I have aquired from these events. 
    </h4>
    <ul>
        <li>
            Controlled event logistics such as registration, permits, police coordination, recruiting and managing volunteers, set up and tear down
        </li>
        <li>
            Procured all equipment and services needed for events including t-shirts, medals, food, and goody bags
        </li>
        <li>
            Compiled event budgets, financial reconciliation, and post-event recaps. 
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