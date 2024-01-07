<script lang="ts">
    import '../app.postcss';
    import {AppShell} from '@skeletonlabs/skeleton';
    import { TabGroup, TabAnchor } from '@skeletonlabs/skeleton';
    import { page } from '$app/stores';

    const mainPages: Array<string> = [
      "about",
      "experience",
      "education",
      "skills",
      "projects",
    ]

    // Highlight JS
    // import hljs from 'highlight.js/lib/core';
    // import 'highlight.js/styles/github-dark.css';
    // import {storeHighlightJs} from '@skeletonlabs/skeleton';
    // import xml from 'highlight.js/lib/languages/xml'; // for HTML
    // import css from 'highlight.js/lib/languages/css';
    // import javascript from 'highlight.js/lib/languages/javascript';
    // import typescript from 'highlight.js/lib/languages/typescript';
    //
    // hljs.registerLanguage('xml', xml); // for HTML
    // hljs.registerLanguage('css', css);
    // hljs.registerLanguage('javascript', javascript);
    // hljs.registerLanguage('typescript', typescript);
    // storeHighlightJs.set(hljs);
</script>

<AppShell>
  <svelte:fragment slot="sidebarLeft">
    <div class="bg-surface-100-800-token hidden h-full items-center justify-center px-28 md:grid ">
      <div class="grid justify-center gap-4">
        {#each mainPages as pageName}
          <div>
            <a href="{pageName}" class="text-xl" class:bg-primary-active-token={$page.url.pathname === `/${pageName}`}>{pageName}</a>
          </div>
        {/each}
      </div>
    </div>
  </svelte:fragment>
    
  <svelte:fragment slot="header">
    <TabGroup 
      justify="justify-center"
      active="variant-filled-primary"
      hover="hover:variant-soft-primary"
      flex="flex-1 lg:flex-none"
      rounded=""
      border=""
      class="bg-surface-100-800-token w-full md:hidden"
    >
      {#each mainPages as pageName}
        <TabAnchor href={pageName} selected={$page.url.pathname === `/${pageName}`}>
          <svelte:fragment slot="lead">(icon)</svelte:fragment>
          <span>{pageName}</span>
        </TabAnchor>
      {/each}
    </TabGroup>
  </svelte:fragment>

  <main class="px-28">
    <slot />
  </main>
</AppShell>
