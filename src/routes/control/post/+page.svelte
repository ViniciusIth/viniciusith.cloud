<script>
    import { Carta, MarkdownEditor } from "carta-md";
    import { code } from "@cartamd/plugin-code";
    import "@cartamd/plugin-code/default.css";

    const carta = new Carta({
        sanitizer: (t) => t,
        extensions: [
            code({
                langs: ["svelte", "js", "java", "go", "docker", "yaml", "c#"],
            }),
        ],
    });

    let value = $state("");

</script>

<MarkdownEditor theme="dracula" {carta} bind:value />

<!-- svelte-ignore css_unused_selector -->
<style lang="scss">
    :global(.carta-editor) {
        :global(textarea) {
            caret-color: black;
            caret-shape: underscore;
            height: 100%;
            padding: 0.5rem !important;
        }

        :global(.carta-highlight) {
            padding: 0.5rem !important;
        }

        :global(.carta-input) {
            background: #0000000f;
            padding: 0;

            border-right: 1px solid #000000;
        }

        :global(.carta-renderer) {
            background: #0000000f;
            padding: 1rem;
            border-left: 1px solid #000000;
        }
    }
</style>
