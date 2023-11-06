<script setup>
import { NOTFOUNT_IMAGE_PATH } from '@/utils/constants';
</script>
<template>
    <Header></Header>
    <div class="container not-found">
        <div>
            <img :src="NOTFOUNT_IMAGE_PATH" alt="Page not Found">
        </div>
    </div>
</template>
<style>
.not-found {
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>