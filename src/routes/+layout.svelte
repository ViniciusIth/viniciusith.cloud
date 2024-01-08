<script lang="ts">
    import '../app.postcss';
    import {AppShell} from '@skeletonlabs/skeleton';
    import { page } from '$app/stores';
    import { LightSwitch } from '@skeletonlabs/skeleton';

    const mainPages: Array<string> = [
      "resume",
      "projects",
      "blog",
    ]
</script>

<AppShell>
  <svelte:fragment slot="sidebarLeft">
    <div class="hidden h-full items-center px-44 grid-rows-[1fr_auto] border-r border-surface-500-400-token md:grid">
      <div class="items-center md:grid">
        <div class="grid gap-4">
          {#each mainPages as pageName}
            <a href="{pageName}" class="text-xl" class:bg-primary-active-token={$page.url.pathname === `/${pageName}`}>{pageName}</a>
          {/each}
        </div>
      </div>
      <LightSwitch class="justify-self-center mb-5"/>
    </div>
  </svelte:fragment>
  <slot/>
</AppShell>
