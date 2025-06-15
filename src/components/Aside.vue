<script>
import HomePage from './HomePage.vue';
import About from './About.vue';
</script>
<template>
    <div class="drawer lg:drawer-open">
        <input id="my-drawer-2" type="checkbox" class="drawer-toggle" />
        <div class="drawer-content flex flex-col items-center justify-center">
            <!-- Page content here -->
            <label for="my-drawer-2" class="btn btn-primary drawer-button lg:hidden">
                Open drawer
            </label>
        </div>
        <div class="drawer-side">
            <label for="my-drawer-2" aria-label="close sidebar" class="drawer-overlay"></label>
            <ul class="menu bg-base-200 text-base-content min-h-full w-80 p-4">
                <!-- Sidebar content here -->
                <router-link to="/" class="text-blue-600 font-semibold">Home</router-link>
                <router-link to="/about" class="text-blue-600 font-semibold">About</router-link>
            </ul>
        </div>
    </div>
</template>