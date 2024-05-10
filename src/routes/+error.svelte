<script>
    import { page } from "$app/stores";
    import tentacles from "$lib/octopus_tentacles.png";
</script>

<svelte:head>
    <title>ViniciusIth - Not Found</title>
</svelte:head>

<div
    class="h-full mt-10 max-h-full overflow-hidden my-auto p-5 text-center bg-surface-50 rounded-container-token container dark:bg-surface-800"
>
    <h1 class="h2 mb-2">Here be Octopus</h1>

    <h2 class="h4">{$page.status} {$page.error?.message}</h2>

    {#if $page.status === 404}
        <h2 class="h4">
            This page doesn't exist or isn't publicaly available yet. <br />
            <a href="/" class="anchor">Go back to main page?</a>
        </h2>
    {:else if $page.status === 500}
        <h2 class="h3">
            Something went wrong, this will be fixed as soon as I notice. <br />
            <a href="/" class="anchor">Go back to main page?</a>
        </h2>
    {/if}
</div>
<img
    src={tentacles}
    alt=""
    class="fixed -bottom-5 left-2/4 -translate-x-1/2 rotate-90 select-none blur-[0.3px] z-[-1]"
    width="460px"
/>
