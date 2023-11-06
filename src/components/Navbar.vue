<script setup>
import { LOGO_ICON_PATH, SCHEDULE_ICON_PATH, LEADERBOARD_ICON_PATH, FLAGAPI_URL } from '@/utils/constants';
</script>
<template>
    <nav class="container navbar">
        <div>
            <img :src="LOGO_ICON_PATH" alt="Logo" />
        </div>
        <div class="link-items">
            <RouterLink class="link-item" to="/schedule">
                <img :src="SCHEDULE_ICON_PATH" class="icon" />
                <p>Schedule</p>
            </RouterLink>
            <RouterLink class="link-item" to="/leaderboard">
                <img :src="LEADERBOARD_ICON_PATH" class="icon" />
                <p>Leaderboard</p>
            </RouterLink>
        </div>
    </nav>
</template>

<style>
.navbar {
    height: 60px;
    background-color: #025FEB;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.link-items {
    display: flex;
    font-size: 216x;
    font-family: 'Open Sans', sans-serif;
}

.link-item {
    text-decoration: none;
    color: white;
    padding-left: 40px;
    display: flex;
    align-items: center;
}

.icon {
    height: 25px;
    width: auto;
}
</style>