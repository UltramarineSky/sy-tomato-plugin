<script lang="ts">
    import { Plugin, Dialog } from "siyuan";
    import { DestroyManager } from "./libs/destroyer";
    import { onMount } from "svelte";
    import { OpenSyFile2 } from "./libs/docUtils";
    import { RPType } from "./ReadingPointBox";

    interface Props {
        plugin: Plugin;
        dialog: Dialog;
        dm: DestroyManager;
        doms: RPType[];
    }

    let {
        plugin,
        dialog,
        dm,
        doms
    }: Props = $props();
    onMount(() => {
        plugin;
        dialog;
        dm;
    });
    export function destroy() {}
</script>

<!-- https://learn.svelte.dev/tutorial/if-blocks -->
<div class="protyle-wysiwyg">
    {#each doms as { dom, row, line }}
        {#if row}
            <button
                class="b3-button b3-button--text tomato-button"
                onclick={() => {
                    OpenSyFile2(plugin, row.id);
                    dm.destroyBy();
                }}>{@html line}</button
            >
        {:else}
            {@html dom}
        {/if}
    {/each}
</div>
