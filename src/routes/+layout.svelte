<script lang="ts">
    import "../app.postcss";
    import { page } from "$app/stores";
    import { onNavigate } from "$app/navigation";
    import {
        Drawer,
        LightSwitch,
        type DrawerSettings,
    } from "@skeletonlabs/skeleton";
    import { initializeStores } from "@skeletonlabs/skeleton";
    import { getDrawerStore } from "@skeletonlabs/skeleton";

    const mainPages: Array<string> = ["resume", "projects", "blog"];

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

    drawerStore.open(drawerSettings);
</script>

<Drawer>
    <div class="grid grid-rows-3 h-full w-72 items-center">
        <!-- <div -->
        <!--     class="grid max-h-screen h-screen w-72 grid-rows-[1fr_1fr] items-end" -->
        <!--     class:hidden={$page.url.pathname === "/"} -->
        <!-- > -->
        <div></div>
        <div class="grid gap-4">
            {#each mainPages as pageName}
                <a
                    href="/{pageName}"
                    class="justify-self-center text-xl"
                    class:bg-primary-active-token={$page.url.pathname ===
                        `/${pageName}`}
                    >{pageName}
                </a>
            {/each}
        </div>
        <LightSwitch class="mb-5 justify-self-center self-end" />
    </div>
</Drawer>

<div class="mx-auto max-w-3xl px-6 py-3 md:px-0 md:py-12">
    <button
        class="btn-icon btn-icon-sm variant-filled-surface mb-3"
        on:click={() => {
            drawerStore.open(drawerSettings);
        }}><span class="material-symbols-outlined"> menu </span></button
    >
    <slot />
</div>
