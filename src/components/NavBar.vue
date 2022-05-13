<template>
    <nav class="navbar">
        <img class="Logo" src="@/assets/Logo.svg" alt='Logo'/>
    </nav>
</template>

<style scoped>
.navbar{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 20px 60px;
    height: auto;
    background: linear-gradient(180deg, #02ADF1 -2.37%, #4562E6 124.84%, #4563E6 124.84%);
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.Logo{
    height: 34px;
    width: 180px;
}
</style>