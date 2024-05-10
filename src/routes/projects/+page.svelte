<script lang="ts">
    import configs from "$lib/projects.json";
    const projects = configs.projects;
</script>

<svelte:head>
    <title>ViniciusIth - Projects</title>
</svelte:head>

<section class="mb-10">
    <h1 class="h1 mb-5">My latest projects</h1>
    <p class="h4">
        Here are some repositories I'm working or have worked on. You can check
        them out on my GitHub profile or by clicking on them.
    </p>
</section>

<section class="grid gap-4 gap-y-10 md:grid-cols-3">
    {#each projects as project}
        <a
            href={project.projectURL}
            target="_blank"
            class="card card-hover p-4"
        >
            <img src={project.imageURL} alt="" class="mb-5 rounded-2xl" />
            <h2 class="h4">{project.title}</h2>
            <p class="line-clamp-3 overflow-hidden text-ellipsis text-justify">
                {@html project.desc}
            </p>
            <hr class="my-5 !border-t-2" />
            <div class="inline">
                {#each project.stacks as stack}
                    <span
                        class="variant-filled-primary chip m-1 rounded-full font-bold"
                        >{stack}</span
                    >
                {/each}
            </div>
            <div class="inline">
                {#each project.tags as tag}
                    <span
                        class="variant-ghost-secondary chip m-1 rounded-full font-bold"
                        >{tag}</span
                    >
                {/each}
            </div>
        </a>
    {/each}
</section>
