<script lang="ts">
    import "../app.postcss";
    import octopus from "$lib/octopus.png";
    import { page } from "$app/stores";
    import { onNavigate } from "$app/navigation";
    import { Drawer, type DrawerSettings } from "@skeletonlabs/skeleton";
    import { initializeStores } from "@skeletonlabs/skeleton";
    import { getDrawerStore } from "@skeletonlabs/skeleton";
    import LightSwitch from "../components/lightswitch.svelte";

    const mainPages: Array<string> = ["projects", "resume", "blog"];

    initializeStores();

    const drawerStore = getDrawerStore();
    const drawerSettings: DrawerSettings = {
        width: "w-auto",
        padding: "pr-4",
        rounded: "rounded-r-xl",
    };

    onNavigate((navigator) => {
        // @ts-expect-error startViewTransition types doesn't exist yet
        if (!document.startViewTransition) return;

        return new Promise((resolve) => {
            // @ts-expect-error startViewTransition types doesn't exist yet
            document.startViewTransition(async () => {
                resolve();
                await navigator.complete;
            });
        });
    });
</script>

<Drawer>
    <div class="grid h-full w-72 grid-rows-3 items-center">
        <a href="/" class="anchor">
            <img src={octopus} class="dark:invert" alt="Go to main page" />
        </a>
        <div class="grid gap-4">
            {#each mainPages as pageName}
                <a
                    href="/{pageName}"
                    class="justify-self-center text-xl"
                    class:anchor={$page.url.pathname !== `/${pageName}`}
                    class:bg-primary-active-token={$page.url.pathname ===
                        `/${pageName}`}
                    >{pageName}
                </a>
            {/each}
        </div>
        <LightSwitch class="mb-5 self-end justify-self-center" />
    </div>
</Drawer>

<div class="mx-auto max-w-3xl py-3 px-5 md:px-0 md:py-12">
    <button
        class="btn-icon btn-icon-sm mb-5 rounded-lg"
        on:click={() => {
            drawerStore.open(drawerSettings);
        }}
    >
        <span>
            <svg
                class="w-5 dark:invert"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 448 512"
                ><!--!Font Awesome Free 6.5.1 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path
                    d="M0 96C0 78.3 14.3 64 32 64H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32C14.3 128 0 113.7 0 96zM0 256c0-17.7 14.3-32 32-32H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32c-17.7 0-32-14.3-32-32zM448 416c0 17.7-14.3 32-32 32H32c-17.7 0-32-14.3-32-32s14.3-32 32-32H416c17.7 0 32 14.3 32 32z"
                /></svg
            >
        </span>
    </button>
    <slot />
</div>
