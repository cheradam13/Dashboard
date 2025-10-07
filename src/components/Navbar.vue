<template>
    <header class="navbar bg-white dark:bg-backgroundDark dark:border-b dark:border-primary/10 sticky top-0 z-10 shadow-sm">
        <nav class="flex-none lg:hidden">
            <label class="btn btn-square btn-ghost" @click="$emit('toggle-drawer')">
                <Icon class="inline-block w-5 h-5" icon="line-md:close-to-menu-alt-transition" />
            </label>
        </nav>

        <section class="flex-1">
            <div class="form-control">
                <input
                    class="input input-bordered w-48 ml-2 md:w-auto dark:bg-white/5 dark:backdrop-blur-md
                    dark:[--webkit-backdrop-filter:blur(10px)] dark:border-white/10"
                    placeholder="Search"
                    type="text"
                >
            </div>
        </section>

        <section class="flex gap-6">
            <!-- Theme Toggle Button -->
            <button
                class="btn btn-ghost btn-circle dark:bg-white/5 dark:backdrop-blur-md
                dark:[--webkit-backdrop-filter:blur(10px)] dark:border-white/10"
                @click="$emit('toggle-theme')"
            >
                <Icon class="w-8 h-8" icon="line-md:moon-alt-to-sunny-outline-loop-transition" v-if="isDark" />
                <Icon class="w-8 h-8" icon="line-md:sunny-outline-to-moon-alt-loop-transition" v-else />
            </button>

            <div class="dropdown dropdown-end">
                <button class="btn btn-ghost btn-circle avatar" tabindex="0" role="button">
                    <div class="w-10 rounded-full">
                        <img src="/public/User.png" alt="User">
                    </div>
                </button>

                <ul
                    class="mt-5 z-[1] p-2 shadow menu menu-sm dropdown-content bg-base-100 rounded-box
                    w-58 space-y-3 dark:bg-backgroundDark **:font-semibold **:text-base"
                    tabindex="0"
                >
                    <li>
                        <a href="#">Profile</a>
                    </li>
                    <li>
                        <a href="#">Settings</a>
                    </li>
                    <li>
                        <a href="#">Logout</a>
                    </li>
                </ul>
            </div>
        </section>
    </header>
</template>
<script setup>
    defineProps({
        isDark: {
            type: Boolean,
            required: true,
        }
    });
    defineEmits(['toggle-drawer', 'toggle-theme']);
</script>