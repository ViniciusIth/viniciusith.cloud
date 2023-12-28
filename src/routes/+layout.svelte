<script lang="ts">
    import '../app.postcss';
    import {AppShell, AppRail, AppRailTile, AppRailAnchor} from '@skeletonlabs/skeleton';
    import { TabGroup, TabAnchor } from '@skeletonlabs/skeleton';
    import { page } from '$app/stores';

    // // Highlight JS
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

<!-- App Shell -->
<AppShell>
  
    <svelte:fragment slot="sidebarLeft">
        <div class="bg-surface-100-800-token hidden w-96 md:block h-full">



    </div>
        <AppRail class="">
            
            <AppRailAnchor href="/" selected={$page.url.pathname === '/'}>(icon)</AppRailAnchor>
            <AppRailAnchor href="/about" selected={$page.url.pathname === '/about'}>(icon)</AppRailAnchor>
          
        
        </AppRail>
    </svelte:fragment>
    
    <svelte:fragment slot="footer">
      <TabGroup 
        justify="justify-center"
        active="variant-filled-primary"
        hover="hover:variant-soft-primary"
        flex="flex-1 lg:flex-none"
        rounded=""
        border=""
        class="bg-surface-100-800-token w-full md:hidden"
      >
        <TabAnchor href="/" selected={$page.url.pathname === '/'}>
          <svelte:fragment slot="lead">(icon)</svelte:fragment>
          <span>(label)</span>
        </TabAnchor>
        <TabAnchor href="/" selected={$page.url.pathname === '/'}>
          <svelte:fragment slot="lead">(icon)</svelte:fragment>
          <span>(label)</span>
        </TabAnchor>
        <TabAnchor href="/" selected={$page.url.pathname === '/'}>
          <svelte:fragment slot="lead">(icon)</svelte:fragment>
          <span>(label)</span>
        </TabAnchor>
      </TabGroup>
    </svelte:fragment>
    
    <slot />
</AppShell>
