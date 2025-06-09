<template>
    <aside class="drawer-side dark:bg-backgroundDark border-r border-gray-200 dark:border-primary/10">
        <label for="my-drawer" aria-label="Close sidebar" class="drawer-overlay"></label>
        <nav class="menu p-4 w-80 min-h-full text-gray-800 dark:texk-gray-200" aria-label="Main navigation">
            <header class="mb-4 flex p-4">
                <h1 class="text-xl font-bold dark:text-white">Admin Panel</h1>
            </header>

            <ul role="menu">
                <li role="none" class="p-2" v-for="(link, index) in links" :key="index">
                    <button role="menuitem" :aria-expanded="!!links.children && links.open"
                        :aria-haspopup="!!link.children" :class="{ 'active': link.active }" @click="setActive(index)"
                        class="flex items-center w-full text-left hover:bg-gray-100 dark:hover:bg-white/10 text-black dark:text-white">
                        <Icon :icon="link.icon" class="h-5 w-5" />
                        <span class="ml-2">{{ link.name }}</span>
                    </button>
                </li>
            </ul>
        </nav>
    </aside>
</template>
<script setup>
import { Icon } from '@iconify/vue'
import { ref } from 'vue'
const links = ref([
    {
        name: 'Dashboard',
        icon: 'line-md:home',
        active: true,
        open: false
    },
    {
        name: 'Analytics',
        icon: 'icon-park-outline:chart-line',
        active: false,
        open: false
    },
    {
        name: 'Reports',
        icon: 'line-md:document-list',
        active: true,
        open: false
    },
    {
        name: 'Users',
        icon: 'line-md:account',
        active: false,
        open: true,
        children: [
            { name: 'All Users' },
            { name: 'Add New User' },
            { name: 'Rules and Permissions' },
        ]
    },
    {
        name: 'Products',
        icon: 'mdi:shopping-outline',
        active: true,
        open: false,
        children: [
            { name: 'All Products' },
            { name: 'Categories' },
            { name: 'Inventory' },
        ]
    },
    {
        name: 'Messages',
        icon: 'line-md:email',
        active: false,
        open: false
    },
    {
        name: 'Settings',
        icon: 'line-md:cog-filled',
        active: true,
        open: false
    }
])
// toggle open state for items with children
const setActive = (index) => {
    if (links.value[index].children) {
        links.value[index].open = !links.value[index].open
    }

    // setting active state

}
</script>