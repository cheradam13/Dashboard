<template>
    <aside class="drawer-side bg-white dark:bg-backgroundDark border-r border-gray-200 dark:border-primary/10">
        <label class="drawer-overlay" for="my-drawer" aria-label="Close sidebar"></label>
        <nav class="menu p-4 w-80 min-h-full text-gray-800 dark:text-gray-200" aria-label="Main navigation">
            <header class="mb-4 flex p-4">
                <h1 class="text-xl font-bold dark:text-white"> AdminPanel</h1>
            </header>

            <ul role="menu">
                <li class="p-2" role="none" v-for="(link, index) in links" :key="index">
                    <button
                        :class="{'active':link.active}"
                        @click="setActive(index)"
                        role="menuitem"
                        :aria-expanded="!!links.children && links.open"
                        :aria-haspopup="!!link.children"
                        class="flex items-center w-full text-left hover:bg-gray-100 dark:hover:bg-white/10 text-black dark:text-white"
                    >
                        <Icon class="h-5 w-5" :icon="link.icon" />
                        <span class="ml-2">{{ link.name }}</span>
                        <span class="ml-auto dropdown-icon">
                            <Icon :icon="link.open ? 'line-md:chevron-down ' : 'line-md:chevron-right'" />
                        </span>
                    </button>

                    <ul class="ml-4 pl-4" v-if="link.children && link.open">
                        <li v-for="(child, childIndex) in link.children" :key="childIndex">
                            <a href="#" class="block py-1 hover:bg-gray-100 dark:hover:bg-white/10 text-black dark:text-white">
                                {{ child.name }}
                            </a>
                        </li>
                    </ul>
                </li>
            </ul>
        </nav>
    </aside>
</template>
<script setup>
    import { ref } from "vue";
    
    const links = ref([
        {
            name: "Dashboard",
            icon: "line-md:home",
            active: true,
            open: false,
        },
        {
            name: "Analytics",
            icon: "icon-park-outline:chart-line",
            active: false,
            open: false,
        },
        {
            name: "Reports",
            icon: "line-md:document-list",
            active: false,
            open: false,
        },
        {
            name: "Users",
            icon: "line-md:account",
            active: false,
            open: true,
            children: [
                {name: "All User"},
                {name: "Add New"},
                {name: "Roles & Permissions"},
            ],
        },
        {
            name: "Products",
            icon: "mdi:shopping-outline",
            active: false,
            open: false,
            children: [
                {name: "All Products"},
                {name: "Categories"},
                {name: "Inventory"},
            ],
        },
        {
            name: "Messages",
            icon: "line-md:email",
            active: false,
            open: false,
            children: [
                {name: "All Products"},
                {name: "Categories"},
                {name: "Inventory"},
            ],
        },
        {
            name: "Settings",
            icon: "line-md:cog-filled",
            active: false,
            open: false,
        },
    ]);

    const setActive = (index) => {
        // Toggle open state for items with children
        if(links.value[index].children) links.value[index].open = !links.value[index].open;

        // Set active state
        links.value.forEach((link, i) => {
            link.active = i === index;
        });
    };
</script>