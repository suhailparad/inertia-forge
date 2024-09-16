<script setup>
import { ref } from 'vue';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
import { Link } from '@inertiajs/vue3';
import {ChartBarIcon,InboxIcon,AcademicCapIcon} from "@heroicons/vue/24/solid"

const showingNavigationDropdown = ref(false);
</script>

<template>
    <div>
        <div class="min-h-screen bg-gray-100 flex">

            <!-- Sidebar Container -->
            <div class="w-[300px] p-6 border-r bg-white">
                 <!-- Logo -->
                <div class="mb-10">
                    <Link :href="route('dashboard')">
                        <ApplicationLogo
                            class="block h-12 w-auto fill-current text-gray-800"
                        />
                    </Link>
                </div>

                <div class="grid mb-6">
                    <div class="text-[12px] text-gray-500  mb-2">ADMINISTRATOR</div>
                    <Link href="/dashboard" class="rounded-lg bg-zinc-600 px-3 py-3 text-white text-[15px] flex items-center gap-1 my-1">
                        <ChartBarIcon class="size-5 text-orange-400" />Dashboard
                    </Link>
                    <Link href="#" class="rounded-lg  px-3 py-3 text-gray-700 text-[15px] flex items-center gap-1  hover:bg-zinc-400 hover:text-white my-1">
                        <InboxIcon class="size-5 text-gray-500 group-hover:text-orange-400" />Messages</Link>
                    <Link href="#" class="rounded-lg  px-3 py-3 text-gray-700 text-[15px] flex items-center gap-1  hover:bg-zinc-400 hover:text-white my-1">
                        <AcademicCapIcon class="size-5 text-gray-500 " /> Academic</Link>
                </div>


            </div>

            <!-- Main page container -->
            <div class="w-full">
                <div class="bg-white border-b h-[70px] p-4 text-end">
                    <div class="ms-3 relative">
                        <Dropdown align="right" width="48">
                            <template #trigger>
                                <span class="inline-flex rounded-md">
                                    <button
                                        type="button"
                                        class="inline-flex items-center px-3 py-2 border border-transparent text-sm leading-4 font-medium rounded-md text-gray-500 bg-white hover:text-gray-700 focus:outline-none transition ease-in-out duration-150"
                                    >
                                        {{ $page.props.auth.user.name }}

                                        <svg
                                            class="ms-2 -me-0.5 h-4 w-4"
                                            xmlns="http://www.w3.org/2000/svg"
                                            viewBox="0 0 20 20"
                                            fill="currentColor"
                                        >
                                            <path
                                                fill-rule="evenodd"
                                                d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                                                clip-rule="evenodd"
                                            />
                                        </svg>
                                    </button>
                                </span>
                            </template>

                            <template #content>
                                <DropdownLink :href="route('profile.edit')"> Profile </DropdownLink>
                                <DropdownLink :href="route('logout')" method="post" as="button">
                                    Log Out
                                </DropdownLink>
                            </template>
                        </Dropdown>
                    </div>
                </div>
                <main>
                    <slot />
                </main>
            </div>

            <!-- Page Content -->
        </div>
    </div>
</template>
