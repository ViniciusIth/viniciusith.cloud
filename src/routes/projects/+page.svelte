<script lang="ts">
    import configs from "$lib/projects.json";
    const projects = configs.projects;
</script>

<svelte:head>
    <title>ViniciusIth - Projects</title>
</svelte:head>

<section class="mb-10">
    <h1 class="h2 mb-5">My latest projects</h1>
    <p>
        Here are some repositories i'm working on or have worked on. You can
        check them out on my GitHub profile.
    </p>
</section>

<section class="grid md:grid-cols-3 gap-4">
    {#each projects as project}
        <a
            href={project.projectURL}
            target="_blank"
            class="card p-4 card-hover"
        >
            <img src={project.imageURL} alt="" class="mb-5 rounded-2xl" />
            <h2 class="h4">{project.title}</h2>
            <p class="overflow-hidden text-ellipsis line-clamp-3 text-justify">{@html project.desc}</p>
            <hr class="!border-t-2 my-5" />
            <div class="inline">
                {#each project.stacks as stack}
                    <span class="chip variant-filled-primary m-1 rounded-full"
                        >{stack}</span
                    >
                {/each}
            </div>
            <div class="inline">
                {#each project.tags as tag}
                    <span class="chip variant-ghost-secondary m-1 rounded-full"
                        >{tag}</span
                    >
                {/each}
            </div>
        </a>
    {/each}
</section>
