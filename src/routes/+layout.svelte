<script lang="ts">
    import "../app.postcss";
    import { AppShell } from "@skeletonlabs/skeleton";
    import { page } from "$app/stores";
    import { fly, blur } from "svelte/transition";
    import { LightSwitch } from "@skeletonlabs/skeleton";
    import { onNavigate } from "$app/navigation";

    const mainPages: Array<string> = ["resume", "projects", "blog"];

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

<AppShell>
    <svelte:fragment slot="sidebarLeft">
        <div
            class="h-full items-center px-36 grid-rows-[1fr_auto] border-r border-surface-500-400-token grid"
            class:hidden={$page.url.pathname === "/"}
        >
            <div class="items-center md:grid">
                <div class="grid gap-4">
                    {#each mainPages as pageName}
                        <a
                            href="/{pageName}"
                            class="text-xl"
                            class:bg-primary-active-token={$page.url
                                .pathname === `/${pageName}`}>{pageName}</a
                        >
                    {/each}
                </div>
            </div>
            <LightSwitch class="justify-self-center mb-5" />
        </div>
    </svelte:fragment>

    <div
        class="container px-44 py-12"
        in:fly={{ x: -200, duration: 300, delay: 300 }}
        out:blur={{ duration: 300 }}
    >
        <slot />
    </div>
</AppShell>
